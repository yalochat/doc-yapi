
# Group Location

This service translate human addresses to geographic coordinates like latitude/longitude and vice versa. This helps to calculate the distance from a client to the stores nearby.

## Translate Geographic Coordinates [/{cc}/location?location={LatLonPair}]

This receives a geographic coordinate and try to return a human readable address.

+ Parameters
    :[cc parameter](parameters.md countryCode:)
    + location (required) - This a geographic coordinate in the format "latitude,longitude", for example, location=19.454886,-99.1758911

### Get  [GET]

+ Response 200 (application/json)

        {
            address: "Mar Mediterráneo 220, Nextitla, 11420 Ciudad de México, D.F., Mexico"
        }

## Translate Human Address [/{cc}/location?address={address}]

Given a human readable address, returns a geographic coordinate.

+ Parameters
    :[cc parameter](parameters.md countryCode:)
    + address (required) - The street address that you want to translate, in the format used by the national postal service of the country concerned. Additional address elements such as business names and unit, suite or floor numbers should be avoided.

### Get [GET]

+ Response 200 (application/json)

        {
            lat: 19.4099711,
            lon: -99.1703208
        }
