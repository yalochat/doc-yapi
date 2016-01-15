
# Group Stores
All stores resources are located under the country code value path.

## Stores Collection [/{cc}/stores{?location,category}]
The stores collection allow to get information for over physical stores subscribed to Yalo. If a GET request is performed over the root stores resource you should get a collection of all the registered stores on a specific country.

+ Parameters
    :[cc parameter](parameters.md countryCode:)
    + location (optional) - This is a geographic coordinate in the format "latitude,longitude", works like a filter to show only the stores that are near the given geographic coordinate.
    + category (optional) - This has to be a valid category ID, it returns stores of the given category.

### Get Stores [GET]

+ Response 200 (application/hal+json)

        {
            total: 113,
            _links: {
                self: {
                    href: "http://api.yalochat.com/mx/stores?location=19.423344,-99.132821"
                }
            },
            _embedded: {
                stores: [
                    {
                        name: "Cocina Economica Los Antojitos",
                        title: "Cocina Economica Los Antojitos - DF - IZTAPALAPA",
                        description: "",
                        url: "",
                        logo: "",
                        photos: {
                            listing: {
                                big: "",
                                small: ""
                            },
                            profile: {
                                big: "",
                                small: ""
                            }
                        },
                        location: {
                            lat: 19.42374,
                            lon: -99.132721,
                            distance: 45.47
                        },
                        address: {
                            formatted: "FRAY SERVANDO TERESA DE MIER 142 B2",
                            region: {
                                name: "Distrito Federal",
                                id: "distrito-federal",
                                slug: "distrito-federal"
                            },
                            city: {
                                name: "IZTAPALAPA",
                                id: "distrito-federal_iztapalapa",
                                slug: "iztapalapa"
                            },
                            country: {
                                name: "México",
                                id: "mx"
                            },
                            postalCode: "09890",
                            zone: {
                                id: "distrito-federal_iztapalapa_benito-juarez",
                                slug: "benito-juarez",
                                name: "BENITO JUAREZ"
                            }
                        },
                        verified: false,
                        financing: "",
                        rating: 0,
                        chatRating: 0,
                        amenities: [
                        "Comida Para Llevar",
                        "Promociones",
                        "Entrega A Domicilio",
                        "Desayunos",
                        "Servicio De Banquetes",
                        "Facilidades Para Personas Discapacitadas"
                        ],
                        schedule: [
                            {
                                days: [
                                    1,
                                    2,
                                    3,
                                    4,
                                    5,
                                    6,
                                    7
                                ],
                                hours: [
                                    [
                                        "0800",
                                        "1800"
                                    ]
                                ]
                            }
                        ],
                        tags: [
                            ""
                        ],
                        timezone: "America/Mexico_City",
                        operators: [
                            "service@yalochat.com",
                            "cocina-economica-los-antojitos.mx"
                        ],
                        id: "cocina-economica-los-antojitos",
                        isOpen: true,
                        _links: {
                            self: {
                                href: "http://api.yalochat.com/mx/stores/cocina-economica-los-antojitos?location=19.423344,-99.132821"
                            }
                        },
                        _embedded: {
                            categories: [
                                {
                                    id: "restaurantes",
                                    name: "Restaurantes",
                                    images: {
                                        logo: "https://storage.googleapis.com/yalo-img/categories/logo_restaurantes.png",
                                        icon: "https://storage.googleapis.com/yalo-img/categories/icon_restaurantes.png",
                                        pin: "https://storage.googleapis.com/yalo-img/categories/pin_restaurantes.png",
                                        photo: "https://storage.googleapis.com/yalo-img/categories/cat_restaurantes.jpg"
                                    }
                                }
                            ]
                        }
                    },
                    {
                        name: "Pizzas Betos",
                        title: "Pizzas Betos - DF - MEXICO",
                        description: "",
                        url: "",
                        logo: "http://graficos.menumania.com.mx/contentstore/43/1941043_V1-E57754018.jpg",
                        photos: {
                            listing: {
                                big: "",
                                small: ""
                            },
                            profile: {
                                big: "",
                                small: ""
                            }
                        },
                        location: {
                            lat: 19.424622,
                            lon: -99.131605,
                            distance: 196.38
                        },
                        address: {
                            formatted: "MIGUEL SCHULTZ 20 - B",
                            region: {
                                name: "Distrito Federal",
                                id: "distrito-federal",
                                slug: "distrito-federal"
                            },
                            city: {
                                name: "MEXICO",
                                id: "distrito-federal_mexico",
                                slug: "mexico"
                            },
                            country: {
                                name: "México",
                                id: "mx"
                            },
                            postalCode: "06470",
                            zone: {
                                id: "distrito-federal_mexico_san-rafael",
                                slug: "san-rafael",
                                name: "SAN RAFAEL"
                            }
                        },
                        verified: false,
                        financing: "",
                        rating: 0,
                        chatRating: 0,
                        amenities: [
                            ""
                        ],
                        schedule: [
                            {
                                days: [
                                    1,
                                    2,
                                    3,
                                    4,
                                    5,
                                    6,
                                    7
                                ],
                                hours: [
                                    [
                                        "0100",
                                        "2200"
                                    ]
                                ]
                            }
                        ],
                        tags: [
                            ""
                        ],
                        timezone: "America/Mexico_City",
                        operators: [
                            "service@yalochat.com",
                            "pizzas-betos.mx"
                        ],
                        id: "pizzas-betos",
                        isOpen: true,
                        _links: {
                            self: {
                                href: "http://api.yalochat.com/mx/stores/pizzas-betos?location=19.423344,-99.132821"
                            }
                        },
                        _embedded: {
                            categories: [
                                {
                                    id: "restaurantes",
                                    name: "Restaurantes",
                                    images: {
                                        logo: "https://storage.googleapis.com/yalo-img/categories/logo_restaurantes.png",
                                        icon: "https://storage.googleapis.com/yalo-img/categories/icon_restaurantes.png",
                                        pin: "https://storage.googleapis.com/yalo-img/categories/pin_restaurantes.png",
                                        photo: "https://storage.googleapis.com/yalo-img/categories/cat_restaurantes.jpg"
                                    }
                                }
                            ]
                        }
                    }
                ]
            }
        }

## Store [/{cc}/stores/{storeId}{?location}]
Given a valid store ID, this endpoint returns a json formatted response containing the store data.

+ Parameters
    :(cc parameter)[parameters.md countryCode:]
    + storeId: `best-buy-df-satelite` (required, string) - The store id is an unique store identifier
    + location (optional) - This is a geographic coordinate in the format "latitude,longitude", if specified, the distance between the client(the given geographic coordinate) and the store is included in the response.

### Get Store [GET]

+ Response 200 (application/hal+json)

        {
            name: "Pizza del Perro Negro",
            title: "Pizza del Perro Negro",
            description: "La Mejor Pizza, punto.",
            url: "http://www.pizzadelperronegro.com/",
            phone: "52 55 5533 9240",
            logo: "",
            photos: {
                listing: {
                    big: "https://irs2.4sqi.net/img/general/width960/36663692_91y9Q_lf_ng0rlSvKkZlch50txiOgxF6szpZFnGfuMY.jpg",
                    small: "https://irs2.4sqi.net/img/general/width960/36663692_91y9Q_lf_ng0rlSvKkZlch50txiOgxF6szpZFnGfuMY.jpg"
                },
                profile: {
                    big: "https://irs2.4sqi.net/img/general/width960/36663692_91y9Q_lf_ng0rlSvKkZlch50txiOgxF6szpZFnGfuMY.jpg",
                    small: "https://irs2.4sqi.net/img/general/width960/36663692_91y9Q_lf_ng0rlSvKkZlch50txiOgxF6szpZFnGfuMY.jpg"
                }
            },
            location: {
                lat: 19.416557,
                lon: -99.169667,
                distance: 3937
            },
            address: {
                formatted: "Parque España 3, Roma Norte, 06700 Ciudad de México, Distrito Federal, México",
                region: {
                    id: "distrito-federal",
                    name: "Distrito Federal",
                    slug: "distrito-federal"
                },
                city: {
                    id: "distrito-federal_ciudad-de-mexico",
                    name: "Ciudad de México",
                    slug: "ciudad-de-mexico"
                },
                country: {
                    id: "mx",
                    name: "México"
                },
                postalCode: "06700",
                zone: {
                    id: "distrito-federal_ciudad-de-mexico_roma-norte",
                    name: "Roma Norte",
                    slug: "roma-norte"
                },
                verified: true
            },
            verified: false,
            financing: "",
            rating: 0,
            chatRating: 0,
            amenities: [ ],
            schedule: [
                {
                    days: [
                        1,
                        2,
                        3,
                        7
                    ],
                    hours: [
                        [
                            "1200",
                            "0000"
                        ]
                    ]
                },
                {
                    days: [
                        4,
                        5,
                        6
                    ],
                    hours: [
                        [
                            "1200",
                            "0100"
                        ]
                    ]
                }
            ],
            tags: [
                "Pizza",
                "Cerveza"
            ],
            timezone: "America/Mexico_City",
            operators: [
                "service@yalochat.com",
                "pizza-del-perro-negro.mx"
            ],
            id: "pizza-del-perro-negro",
            _links: {
                self: {
                    href: "http://api.yalochat.com/mx/stores/pizza-del-perro-negro?location=19.423344,-99.132821"
                }
            },
            isOpen: true,
            _embedded: {
                categories: [
                    {
                        id: "restaurantes",
                        name: "Restaurantes",
                        images: {
                            logo: "https://storage.googleapis.com/yalo-img/categories/logo_restaurantes.png",
                            icon: "https://storage.googleapis.com/yalo-img/categories/icon_restaurantes.png",
                            pin: "https://storage.googleapis.com/yalo-img/categories/pin_restaurantes.png",
                            photo: "https://storage.googleapis.com/yalo-img/categories/cat_restaurantes.jpg"
                        }
                    }
                ]
            }
        }

## Is Store Open? [/{cc}/stores/{storeId}/is-open]
Given a valid store ID, this endpoint indicates if a store is open in the moment when the request is made.

+ Parameters
    :(cc parameter)[parameters.md countryCode:]
    + storeId: `best-buy-df-satelite` (required, string) - The store id is an unique store identifier

### Is Open [GET]

+ Response 200 (application/hal+json)

        {
            id: "pizza-del-perro-negro",
            isOpen: true,
            _links: {
                self: {
                    href: "http://api.yalochat.com/mx/stores/pizza-del-perro-negro"
                }
            }
        }
