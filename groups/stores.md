
# Group Stores
All stores resources are located under the country code value path.

## Stores Collection [/{cc}/stores]
The stores collection allow to get information for over physical stores subscribed to Yalo. If a GET request is performed over the root stores resource you should get a collection of all the registered stores on a specific country.

+ Parameters
    :[cc parameter](parameters.md countryCode:)

### Get Stores [GET]

+ Response 200 (application/hal+json)

        {
            "total": 2,
            "_links": {
                "self": {"href":"http://api.ayalo.co/mx/stores?category=electronicos&location=19.433103,-99.181750"}
            },
            "_embedded": {
                "stores": [
                    {
                        "id": "best-buy-satelite",
                        "name": "Best Buy Satelite",
                        "title": "Best Buy - DF - Satelite",
                        "description": "Compañía que ofrece productos electronicos",
                        "url": "http://www.bestbuy.mx/",
                        "logo": "http://tools.ayalo.co/210602_elektra-logo.jpg",
                        "photos": {
                            "listing":{
                                "big": "https://yaloquiero.mx/img/temp/stores_01.png",
                                "small": "https://yaloquiero.mx/img/temp/stores_01.png"
                            },
                            "profile": {
                                "big": "https://yaloquiero.mx/img/temp/storeprofile_01.png",
                                "small": "https://yaloquiero.mx/img/temp/storeprofile_01.png"
                            }
                        },
                        "location": {
                            "distance": 250,
                            "lat" : 19.435211,
                            "lon" : -99.185434
                        },
                        "address": {
                            "formatted": "Circuito Centro Comercial #2251 CD. Satelite Local 22 Segundo Nivel",
                            "region": {
                                "id":"df",
                                "name":"Distrito Federal"
                            },
                            "city": {
                                "id":"satelite",
                                "name":"Ciudad Satelite"
                            },
                            "country": {
                                "id":"mx",
                                "name":"Mexico"
                            },
                            "postal_code": "12345"
                        },
                        "verified": true,
                        "financing": "Financing description",
                        "rating": 4.7,
                        "chat_rating": 4.1,
                        "amenities": [
                            "credit_card",
                            "take_out",
                            "parking"
                        ],
                        "schedule": [{
                            "days": [
                                1,
                                3,
                                5
                            ],
                            "hours": [
                                ["0800", "1300"],
                                ["1400", "2000"]
                            ]
                        }],
                        "tags": [
                            "cargador-apple",
                            "video-juegos",
                            "televisores"
                        ],
                        "_links": {
                            "self": {"href":"http://api.yalo.co/mx/stores/best-buy-satelite"}
                        },
                        "_embedded": {
                            "categories": [{
                                "id": "electronicos" ,
                                "name": "Electronicos",
                                "photo": "https://yaloquiero.mx/img/temp/storeprofile_01.png",
                                "_links": {
                                    "self": {"href":"http://api.yalo.co/mx/categories/electronicos"}
                                }
                            }]
                        }
                    },
                    {
                        "id": "walmart-satelite",
                        "name": "Walmart satelite",
                        "title": "Walmart - DF - Satelite",
                        "description": "Cadena de supermercados mas grande del mundo",
                        "url": "http://www.walmart.mx/",
                        "logo": "http://tools.ayalo.co/210602_walmart.jpg",
                        "photos": {
                            "listing":{
                                "big": "https://yaloquiero.mx/img/temp/stores_02.png",
                                "small": "https://yaloquiero.mx/img/temp/stores_02.png"
                            },
                            "profile": {
                                "big": "https://yaloquiero.mx/img/temp/storeprofile_02.png",
                                "small": "https://yaloquiero.mx/img/temp/storeprofile_02.png"
                            }
                        },
                        "location": {
                            "distance": 375,
                            "lat" : 19.441466,
                            "lon" : -99.183322
                        },
                        "address": {
                            "formatted": "Camino San Juan de Aragón 516, Ciudad de México, DF‎",
                            "region": {
                                "id":"df",
                                "name":"distrito federal"
                            },
                            "city": {
                                "id":"eduardo-molina",
                                "name":"Eduardo Molina"
                            },
                            "country": {
                                "id":"mx",
                                "name":"Mexico"
                            },
                            "postal_code": "12345"
                        },
                        "verified": true,
                        "financing": "financing description",
                        "rating": 4.5,
                        "chat_rating": 4.6,
                        "amenities": [
                            "credit_card",
                            "take_out",
                            "parking"
                        ],
                        "schedule": [{
                            "days": [
                                1,
                                2,
                                3,
                                4,
                                5
                            ],
                            "hours": [
                                ["0800", "2200"]
                            ]
                        }],
                        "tags": [
                            "cargador-apple",
                            "video-juegos",
                            "televisores"
                        ],
                        "_links": {
                            "self": {"href":"http://api.yalo.co/mx/stores/walmart-satelite"}
                        },
                        "_embedded": {
                            "categories": [{
                                "id": "electronicos" ,
                                "name": "electronicos",
                                "photo": "https://yaloquiero.mx/img/temp/storeprofile_01.png",
                                "_links": {
                                    "self": {"href":"http://api.yalo.co/mx/categories/electronicos"}
                                }
                            },{
                                "id": "farmacia" ,
                                "name": "Farmacia",
                                "photo": "https://yaloquiero.mx/img/temp/stores_03.png",
                                "_links": {
                                    "self": {"href":"http://api.yalo.co/mx/categories/farmacia"}
                                }
                            }]
                        }
                    }
                ]
            }
        }

## Store [/{cc}/stores/{storeId}]
To get details of a specific Store you must provide the id of a store.

+ Parameters
    :(cc parameter)[parameters.md countryCode:]
    + storeId: `best-buy-df-satelite` (required, string) - The store id is an unique store identifier

### Get Store [GET]

+ Response 200 (application/hal+json)

        {
            "id": "best-buy-satelite",
            "name": "Best Buy Satelite",
            "title": "Best Buy - DF - Satelite",
            "description": "Compañía que ofrece productos electronicos",
            "url": "http://www.bestbuy.mx/",
            "logo": "http://yalo.co/logo-best-buy.png",
            "photos": {
                "listing":{
                    "big": "https://yaloquiero.mx/img/temp/stores_01.png",
                    "small": "https://yaloquiero.mx/img/temp/stores_01.png"
                },
                "profile": {
                    "big": "https://yaloquiero.mx/img/temp/storeprofile_01.png",
                    "small": "https://yaloquiero.mx/img/temp/storeprofile_01.png"
                }
            },
            "location": {
                "distance": 250,
                "lat" : 19.435211,
                "lon" : -99.185434
            },
            "address": {
                "formatted": "Circuito Centro Comercial #2251 CD. Satelite Local 22 Segundo Nivel",
                "region": {
                    "id":"df",
                    "name":"Distrito Federal"
                },
                "city": {
                    "id":"satelite",
                    "name":"Ciudad Satelite"
                },
                "country": {
                    "id":"mx",
                    "name":"Mexico"
                },
                "postal_code": "12345"
            },
            "verified": true,
            "financing": "Financing description",
            "rating": 4.7,
            "chat_rating": 4.1,
            "amenities": [
                "credit_card",
                "take_out",
                "parking"
            ],
            "schedule": [{
                "days": [
                    1,
                    3,
                    5
                ],
                "hours": [
                    ["0800", "1300"],
                    ["1400", "2000"]
                ]
            }],
            "tags": [
                "cargador-apple",
                "video-juegos",
                "televisores"
            ],
            "_links": {
                "self": {"href":"http://api.yalo.co/mx/stores/best-buy-satelite?location=19.433103,-99.181750"}
            },
            "_embedded": {
                "categories": [{
                    "id": "electronicos" ,
                    "name": "Electronicos",
                    "photo": "https://yaloquiero.mx/img/temp/storeprofile_01.png",
                    "_links": {
                        "self": {"href":"http://api.yalo.co/mx/categories/electronicos"}
                    }
                }]
            }
        }
