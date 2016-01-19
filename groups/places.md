
# Group Places

Recources related to coutries, cities and zones.

## List Countries [/countries]

Coutries collection.

### Retrieve all countries [GET]

Retrieves a list of all available countries.

+ Response 200 (application/json)

        [
            {
                "code": "gt",
                "name": "Guatemala",
                "cities": "123"
            },
            {
                "code": "mx",
                "name": "Mexico",
                "cities": "456"
            }
        ]

## Get Country [/countries/{cc}]

Retrieve country data.

+ parameters
    + cc - ISO 2 characters country code

### Get country data [GET]

Get data about a coutry.

+ Response 200 (application/json)

        {
            "code": "gt",
            "self": "http:/api.yalochat.com/countries/gt"
            "name": "Guatemala",
            "cities": "123"
        }

## List Cities [/countries/{cc}/cities]

City collections.

+ parameters
    + cc - ISO 2 characters country code

### Retrieve cities by country [GET]

+ Response 200 (application/json)

        [
            {
                "id": "1",
                "name": "Guatemala city",
                "location": "14.583559, -90.527511",
                "zones": [
                    {
                        "name": "Zona 1",
                        "location": "14.583559, -90.527511"
                    },
                    {
                        "name": "Zona 2",
                        "location": "14.59, -90.6042"
                    }
                ]
            },
            {
                "id": "2",
                "name": "Mixco",
                "location": "14.634350, -90.600236",
                "zones": [
                    {
                        "name": "Zona 1",
                        "location": "14.583559, -90.527511"
                    },
                    {
                        "name": "Zona 2",
                        "location": "14.59, -90.6042"
                    }
                ]
            }
        ]

## Get City [/countries/{cc}/cities/{city_id}]

Retrieve city data.

+ parameters
    + cc - ISO 2 characters country code
    + city_id - City id

### Get city [GET]

+ Response 200 (application/json)

        {
            "id": "1",
            "name": "Guateamala city",
            "location": "14.583559, -90.527511",
            "zones": [
                {
                    "name": "Zona 1",
                    "location": "14.583559, -90.527511"
                },
                {
                    "name": "Zona 2",
                    "location": "14.59, -90.6042"
                }
            ]
        }
