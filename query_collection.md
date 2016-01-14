
# yAPI Query collection

# Group Root resource operations
All root resource, except the status resource, are specified after the country `{cc}` path parameter. A root resource is a business object that can be filter, query and refined.

## Filtering resources
Filters on root resources can be executed purely using URI nested path parameters. For example, in the store resource path param filters helps refine the store physical location.

_Filter examples_
* Filters on `stores`
  - `/{cc}/stores/{region}` _Filter stores by  region_
  - `/{cc}/stores/{region}/{city}` _Filter stores by region and city_
  - `/{cc}/stores/{slug}` _Get a specific store document_

## Searching resources
yApi search allows to execute a search and get back hits that match a string. A search can be performed using a simple search string parameter `q`.

_Search examples_
* Searching over resources
  - `/mx/products?q=motos` _Search for products with th string "motos" on any field._
  - `/gt/companies?q=zona+9` _Search all the companies with the string "zona 9" on any field._

## Querying resources
A query request can be executed using the `q` request parameter in conjuction with a field. Queries are provided with a rich query language through the [Apache Lucene Query Parser](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

### Fields
yAPI supports fielded data. When performing a query you can either specify a field or not.

You can search any field by typing the field name followed by a colon ":" and then the term you are looking for.

As an example, assume you want to search in the store name field. If you want to answer the question, which store is named "Best Buy", you can query:

* `/mx/stores/df?q=name:"Best Buy"` Search for stores in `df` region that contains "Best Buy" in field name.
* `/gt/stores?q=name:best` Search for stores that contains the string "best" in field name.

### Term modifiers

#### Terms
* A query is broken up into terms and operators. There are two types of terms: __Single Terms and Phrases.__
* A Single Term is a single word such as "motos" or "electronicos".
* A Phrase is a group of words surrounded by double quotes such as "foto video".
* Multiple terms can be combined together with Boolean operators to form a more complex query.

#### Wildcards
yAPI supports modifying query terms to provide a wide range of searching options.
A wildcard search or query supports single and multiple character wildcard searches within single terms _(not within phrase queries)_.

* To perform a single character wildcard search use the "?" symbol.
* To perform a multiple character wildcard search use the "*" symbol.

The single character wildcard looks for terms that match with the single character replaced. For example, to search for "camion" or "camión" you can use the search:

* `/mx/products?q=cami?n`

Multiple character wildcard looks for 0 or more matches. For example, to search for "electronicos" or "electrodomesticos", you can use the search:

* `/mx/products?q=electro*`

You can also use the wildcard in the middle of a term.

* `/mx/stores/df/satelite?q=sal?n`

Note wildcards can be slow, as it needs to iterate over many terms.
To prevent extremely slow wildcard queries, a wildcard term should not start with one of the wildcards * or ?.

### Fuzzy
yAPI supports fuzzy searches or queries. To do a fuzzy search use the tilde, "~", symbol at the end of a Single word Term.
For example to search for a term similar in spelling to "plaza" use the fuzzy search:

* `/mx/stores/df?q=plaza~`

### Boolean Operators
Boolean operators allow terms to be combined through logic operators. yAPI supports AND, "+", OR, NOT and "-" as Boolean operators __(Note: Boolean operators must be ALL CAPS)__.
The OR operator is the default conjunction operator. This means that if there is no Boolean operator between two terms, the OR operator is used.
The OR operator links two terms and finds a matching document if either of the terms exist in a document.
The symbol || can be used in place of the word OR.

#### OR
To search for places that contain either "Segusino muebles" or just "muebles" you can use any of these queries:
* `/mx/products?q="Segusino muebles" muebles`
* `/mx/products?q="Segusino muebles" OR muebles`
* `/mx/products?q="Segusino muebles" || muebles`

#### AND
The AND operator matches resources where both terms exist anywhere in the text of a resource.
To search for documents that contain "muebles" and "electrodomesticos" use the query:

* `/mx/products?q=muebles AND electrodomesticos` _Search for products with the word "muebles" and "electrodomesticos"._

#### Required
The "+" or required operator requires that the term after the "+" symbol exist somewhere in a the field.
To search for products that must contain "iphone" and may contain "telefono" use the query:

* `/mx/products?q=+iphone telefonos`

#### NOT

The NOT operator excludes resources that contain the term after NOT. The symbol ! can be used in place of the word NOT.
To search for products that contain "sony" but not "telefono" use the search:

* `/gt/products?q=sony !telefono`
* `/gt/products?q=sony NOT telefono`

__Note:__ The NOT operator cannot be used with just one term. For example, the following search will return no results:

* `/gt/products?q=sony NOT "telefono celular"`

#### Prohibit

The "-" or prohibit operator excludes resources that contain the term after the "-" symbol.
To search for documents that contain "sony" but not "telefono celular" use the query:

* `/gt/products?q=sony -"telefono celular"`

### Grouping
yAPI supports using parentheses to group clauses to form sub queries. This can be very useful if you want to control the boolean logic for a query.

_Example_

* `/gt/products/electronicos?q=(name:telefono OR name:celular) AND (description:huawei OR name:samsung)` _Search for products in electronicos that the field name contains "telefono" or "celular" and the field description contains "huawei" or "samsung"_
* `/gt/products?q=name:(+samsung +"galaxy note")` _Search for products with name that contains "samsing" or "galaxy note"._

## Selective fields
Allows to selectively load specific fields for each resource returned from a request. For select fields you need to add the `fields` query param to your request.

_Example_

* `/gt/products?q=sony&fiels=name,description` _Get the name and description fields for all products with the word "sony"_

* can be used to load all stored fields from nested resource attribute.

* `/gt/products?q=sony&fiels=name,description,category.*` _Get the name, description and all category fields for all products with the word "sony"_
* `/gt/stores/df/satelite?fiels=slug,name,description,company.name,company.description` _Get the name, description and all category fields for all products with the word "sony"_
