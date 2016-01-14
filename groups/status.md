
# Group Status

## Status endpoint [/status]
With this endpoint your are able to know if all the services needed to run the API are working properly.

### Get Status [GET]

+ Response 200 (application/json)

        [
            {
                "country": "gt",
                "query-service":"OK",
                "polices-service":"OK",
                "auth-service":"OK"
            },
            {
                "country": "mx",
                "query-service":"OK",
                "polices-service":"OK",
                "auth-service":"OK"
            }
        ]
