
# Group Search

You can perform a basic search using the "q" query string parameter. The value of the "q" parameter is parsed into *terms* and *operators*.

> The *"q"* parameter is only available in the **stores** and **categories** resources.

A *term* can be a single word, or a phrase surrounded by double quotes -- "guatemalan good" -- which searches for all the words in the phrase, in the same order.

With the *operators* you can customize your search. The available operators are the following.

### Field Names

It is possible to specify fields, like this:

- where the status field contains "active"

    ```
    status:active
    ```
- where the title field contains quick or brown. If you omit the OR operator the default operator will be used

    ```
    title:(quick OR brown)
    ```
- where the author field contains the exact phrase "john smith"

    ```
    author:"John Smith"
    ```
- where the field title has no value (or is missing):

    ```
    _missing_:title
    ```
- where the field title has any non-null value:

    ```
    _exists_:title
    ```

### Ranges
Ranges can be specified for date, numeric or string fields. Inclusive ranges are specified with square brackets [min TO max] and exclusive ranges with curly brackets {min TO max}.

- All days in 2012:

    ```
    date:[2012-01-01 TO 2012-12-31]
    ```
- Numbers 1..5

    ```
    count:[1 TO 5]
    ```
- Tags between alpha and omega, excluding alpha and omega:

    ```
    tag:{alpha TO omega}
    ```
- Numbers from 10 upwards

    ```
    count:[10 TO *]
    ```
- Dates before 2012

    ```
    date:{* TO 2012-01-01}
    ```
- Curly and square brackets can be combined:

    ```
    count:[1 TO 5}
    ```

### Boolean operators
By default, all terms are optional, as long as one term matches. A search for foo bar baz will find any document that contains one or more of foo or bar or baz. There are boolean operators which can be used in the query string itself to provide more control.

The preferred operators are **+** (this term must be present) and **-** (this term must not be present). All other terms are optional. For example, this query:

```
quick brown +fox -news
```

states that:

- fox must be present
- news must not be present

The familiar operators **AND**, **OR** and **NOT** (also written &&, || and !) are also supported. However, the effects of these operators can be more complicated than is obvious at first glance. **NOT** takes precedence over **AND**, which takes precedence over **OR**. While the + and - only affect the term to the right of the operator, **AND** and **OR** can affect the terms to the left and right.

### Grouping
Multiple terms or clauses can be grouped together with parentheses, to form sub-queries:

```
(quick OR brown) AND fox
```

Groups can be used to target a particular field, or to boost the result of a sub-query:

```
status:(active OR pending) title:(full text search)
```

### Reserved characters
If you need to use any of the characters which function as operators in your query itself (and not as operators), then you should escape them with a leading backslash. For instance, to search for (1+1)=2, you would need to write your query as \(1\+1\)\=2.

The reserved characters are: + - = && || > < ! ( ) { } [ ] ^ " ~ * ? : \ /

> Failing to escape these special characters correctly could lead to a syntax error which prevents your query from running.
