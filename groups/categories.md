
# Group Categories
All categories resources are located under the country code value path.

## Categories Collection [/{cc}/categories]
The categories collection allows to get all the available categories in a given country. Stores are grouped by categories.

+ Parameters
    :[cc parameter](parameters.md countryCode:)
    + location (optional) - This is a geographic coordinate in the format "latitude,longitude", works like a filter to show only the categories that have stores near the given geographic coordinate.

### Get Categories [GET]

+ Response 200 (application/hal+json)

        {
            "total": 2,
            "_links": {
                "self": {"href":"http://api.yalochat.com/mx/categories?location=19.414980271831,-99.177446197718"}
            },
            "_embedded": {
                "categories": [
                    {
                        "id": "restaurantes" ,
                        "name": "Restaurantes",
                        images: {
                            logo: "https://storage.googleapis.com/yalo-img/categories/logo_restaurantes.png",
                            icon: "https://storage.googleapis.com/yalo-img/categories/icon_restaurantes.png",
                            pin: "https://storage.googleapis.com/yalo-img/categories/pin_restaurantes.png",
                            photo: "https://storage.googleapis.com/yalo-img/categories/cat_restaurantes.jpg"
                        },
                        _links: {
                            self: {
                                href: "http://api.yalochat.com/mx/categories/restaurantes?location=19.414980271831,-99.177446197718"
                            },
                            stores: {
                                href: "http://api.yalochat.com/mx/stores?location=19.414980271831,-99.177446197718&category=restaurantes"
                            }
                        },
                        "_embedded": {
                            "stores": {
                                "total": 121
                            }
                        }
                    },{
                        id: "cafes",
                        name: "Cafes",
                        images: {
                            logo: "https://storage.googleapis.com/yalo-img/categories/logo_bebidas.png",
                            icon: "https://storage.googleapis.com/yalo-img/categories/icon_cafes.png",
                            pin: "https://storage.googleapis.com/yalo-img/categories/pin_cafes.png",
                            photo: "https://storage.googleapis.com/yalo-img/categories/cat_cafes.jpg"
                        },
                        _links: {
                            self: {
                                href: "http://api.yalochat.com/mx/categories/cafes?location=19.414980271831,-99.177446197718"
                            },
                            stores: {
                                href: "http://api.yalochat.com/mx/stores?location=19.414980271831,-99.177446197718&category=cafes"
                            }
                        },
                        _embedded: {
                            stores: {
                                total: 33
                            }
                        }
                    }
                ]
            }
        }
