
# Group Location

This service translate human addresses to geographic coordinates like latitude/longitude, this helps to calculate the distance from a client to the stores nearby using resources like `stores`.

## Geographic coordinates [/{cc}/location?q={address}]

Given an address, returns a pair or latitude/longitude coordinates.

+ Parameters
    :[cc parameter](parameters.md countryCode:)
    + address (required) - The street address that you want to translate, in the format used by the national postal service of the country concerned. Additional address elements such as business names and unit, suite or floor numbers should be avoided.

### Get latitude/longitude [GET]

+ Response 200 (application/json)

    [14.622362, -90.514406]
