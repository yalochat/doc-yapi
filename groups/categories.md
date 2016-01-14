
# Group Categories
All categories resources are located under the country code value path.

## Categories Collection [/{cc}/categories]
The categories collection allows to get all the available categories in a given country. Stores are grouped by categories.

+ Parameters
    :[cc parameter](parameters.md countryCode:)

### Get Categories [GET]

+ Response 200 (application/hal+json)

        {
            "total": 2,
            "_links": {
                "self": {"href":"http://api.ayalo.co/v1/mx/categories"}
            },
            "_embedded": {
                "categories": [
                    {
                        "id": "electronicos" ,
                        "name": "Electronicos",
                        "photo": "http://img.ayalo.co/electronicos.png",
                        "_links": {
                            "self": {"href":"http://api.yalo.co/v1/mx/categories/electronicos"}
                        },
                        "_embedded": {
                            "stores": {
                                "total": 3,
                                "_links": {"href":"http://api.yalo.co/v1/mx/stores"},
                                "_embedded": {
                                    "stores":[{
                                        "id": "best-buy-satelite",
                                        "name": "Best Buy Satelite",
                                        "description": "Compañía que ofrece productos electronicos",
                                        "logo": "http://yalo.co/logo-best-buy.png"
                                    },{
                                        "id": "walmart-satelite",
                                        "name": "Walmart Satelite",
                                        "description": "Cadena de supermercados mas grande del mundo",
                                        "logo": "http://yalo.co/walmart-buy.png"
                                    }]
                                }    
                            }
                        }
                    },{
                        "id": "farmacia" ,
                        "name": "Farmacia",
                        "photo": "http://img.ayalo.co/farmacia.png",
                        "_links": {
                            "self": {"href":"http://api.yalo.co/v1/mx/categories/farmacia"}
                        },
                        "_embedded": {
                            "stores": {
                                "total": 3,
                                "_links": {"href":"http://api.yalo.co/v1/mx/stores"},
                                "_embedded": {
                                    "stores":[{
                                        "id": "walmart-satelite",
                                        "name": "Walmart Satelite",
                                        "description": "Cadena de supermercados mas grande del mundo",
                                        "logo": "http://yalo.co/walmart-buy.png"
                                    }]
                                }    
                            }
                        }
                    }
                ]
            }
        }


## Category [/{cc}/categories/{categoryId}]
To get details of a specific category just provide the category id.

+ Parameters
    :[cc parameter](parameters.md countryCode:)
    + categoryId: `electronicos` (required, string) - The category id is unique identifier

### Get Category [GET]

+ Response 200 (application/hal+json)

        {
            "id": "electronicos" ,
            "name": "Electronicos",
            "photo": "http://img.ayalo.co/electronicos.png",
            "_links": {
                "self": {"href":"http://api.yalo.co/v1/mx/categories/electronicos"}
            },
            "_embedded": {
                "stores": {
                    "_links": {"href":"http://api.yalo.co/v1/mx/stores"}
                }
            }
        }
