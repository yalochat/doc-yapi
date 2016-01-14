FORMAT: 1A
HOST: http://api.ayalo.co/v1

# Yalo Query Base yAPI

yAPI is query oriented API that allows Ayalo client applications to access the core business on behalf of users to perform a variety of complex queries over stores, locations and products and other resource.

To familiarize with yAPI, you can browse through all this detail documentation.

This document was build ussing a cookbook style and will guide you through the most common and simple query tasks to yAPI expert.
It's designed to start from the basics and slowly increase sophisticated concepts until you know everything there is to know about querying over yAPI.

These guides are written in Markdown and are available on our private git [repo](ayalo.bitbucket.org). If there is something missing, or you find a typo or mistake, please help us by filing an issue or submitting a pull request. Thanks!

# Overview

yAPI is designed and optimized for queries over a just few core business objects or resources.
The yAPI search engine provides the power of a speed search with a sophisticated, developer-friendly query language.

Through yAPI it's possible to access Ayalo locations, stores, products, categories and others.
The API is based in the idea that each resource or collection is stored in a specific path where it's possible to do filtering and search.

For example, pay attention to the next URL.
`api.ayalo.co/v1/mx/stores/df/satelite/`
This path represent all the stores that are physically located at Mexico, Distrito Federal region , Satelite city.

:[Group Authentication](groups/oauth.md)

:[Query Collection](query_collection.md)

<!---
## Aggregations WIP
An aggregation can be seen as a unit-of-work that builds analytic information over a set of documents.

## Embedding resources WIP
An aggregation can be seen as a unit-of-work that builds analytic information over a set of documents.

## Pagination WIP
An aggregation can be seen as a unit-of-work that builds analytic information over a set of documents.
-->

<!-- :[Group Status](groups/status.md) -->

:[Group Location](groups/location.md)

<!-- :[Group Companies](groups/companies.md) -->

:[Group Stores](groups/categories.md)

:[Group Stores](groups/stores.md)

<!-- :[Group Places](groups/places.md) -->

<!-- :[Group Products](groups/products.md) -->
