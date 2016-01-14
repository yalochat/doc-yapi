
# Group Companies

All companies resources are located under the country code value path.
A company must have at least one store. To get the collection of stores by company you can use the `stores` resource filtering by company.

## Companies Collection [/{cc}/companies]
The companies collection allows to get information for over companies that have stores subscribed to Ayalo. If a GET request is performed over the root companies resource you should get a collection of all the registered companies on a specific country.

+ Parameters
    + cc (required, string) - ISO 2 characters country code

### Get available companies [GET]

+ Response 200 (application/json)

        [
            {
                "id":986,
                "slug":"best-buy",
                "name":"Best Buy",
                "links": {
                    "self": "http://api.ayalo.co/v1/mx/companies/best-buy"
                },
                "title":"Best Buy - Mexico",
                "logo": {
                  "small": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/best-buy-small.png",
                  "medium": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/best-buy-medium.png",
                  "large": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/best-buy-large.png"
                },
                "description": "Compañía que ofrece productos electronicos",
                "phone":"5374-0108",
                "active": true,
                "sell_online": true,
                "url": "httpd://www.bestbuy.mx/",
                "chat_rating": 4.4,
                "tags": [
                    "cargador-apple",
                    "video-juegos",
                    "televisores"
                ],
                "country": {
                    "code":"mx",
                    "name":"Mexico",
                    "url": "http:/api.ayalo.co/v1/countries/mx"
                },
                "stores": "http:/api.ayalo.co/v1/mx/stores?q=company:best-buy"
            },
            {
                "id":786,
                "slug":"walmart",
                "name":"Walmart",
                "links": {
                    "self": "http://api.ayalo.co/v1/mx/companies/walmart",
                    "stores": "http:/api.ayalo.co/v1/mx/stores?q=company:walmart"
                },
                "title":"Walmart - Mexico",
                "logo": {
                  "small": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/walmart-small.png",
                  "medium": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/walmart-medium.png",
                  "large": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/walmart-large.png"
                },
                "description": "Biggest retail corporation in the world.",
                "phone":"9875-4567",
                "active": true,
                "sell_online": false,
                "url": "http://www.walmart.mx",
                "chat_rating": 4.3,
                "tags": [
                    "alimento",
                    "articulo-limpieza",
                    "refrezco"
                ],
                "country": {
                    "code":"mx",
                    "name":"Mexico",
                    "links": {
                        "self": "http:/api.ayalo.co/v1/countries/mx"
                    }
                }
            }
        ]

## Company [/{cc}/companies/{company_slug}]
Retrieve a company data

+ Parameters
    + cc (required, string) - ISO 2 characters country code
    + company_slug (required) - A company slug

### Get company [GET]

+ Response 200 (application/json)

        {
            "id":986,
            "slug":"best-buy",
            "name":"Best Buy",
            "self":"http://api.ayalo.co/v1/mx/companies/best-buy",
            "title":"Best Buy - Mexico",
            "logo": {
              "small": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/best-buy-small.png",
              "medium": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/best-buy-medium.png",
              "large": "https://s3.amazonaws.com/assets.ayalo.co/mx/logos/best-buy-large.png"
            },
            "description": "Compañía que ofrece productos electronicos",
            "phone":"5374-0108",
            "active": true,
            "sell_online": true,
            "url": "httpd://www.bestbuy.mx/",
            "chat_rating": 4.4,
            "tags": [
                "cargador-apple",
                "video-juegos",
                "televisores"
            ],
            "country": {
                "code":"mx",
                "name":"Mexico",
                "links": {
                    "self": "http:/api.ayalo.co/v1/countries/mx"
                }
            },
            "stores": "http:/api.ayalo.co/v1/mx/stores?q=company:best-buy"
        }
