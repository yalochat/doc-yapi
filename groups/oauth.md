
# Authentication and Authorization

yAPI uses OAuth2 to allow authenticated access to private resources and business objects.

OAuth2 is a protocol that lets external apps request authorization to private details in a Yalo user’s account without getting their password. This is preferred over Basic Authentication because tokens can be limited to specific types of data, and can be revoked by users at any time.

All Yalo internal and external applications need to register their application before getting started. A registered OAuth application is assigned a unique Client ID and Client Secret. The Client Secret should not be shared.

## Terms to know

### Client (application)
It can be an app running on a mobile device or a web app. The app makes requests to the resource server for protected assets on behalf of the resource owner. The resource owner must give the app permission to access the protected resources.

### Resource owner
Also called an "end user". This is generally the person (or other entity) who is capable of granting access to a protected resource. For example, if an app needs to use chat messages or email address, then you are the resource owner and the only person who can grant the app access to your data.

### Resource server
The resource server is the yAPI platform who stores and manage user and business resources. The yAPI platform need to perform authorization steps before it will serve up protected resources to and application client.

### Authorization server
Yalo authorization server is implemented in compliance with the OAuth 2.0 specification, and it is responsible for validating authorization grants and issuing the access tokens that give the app access to the user's data on yAPI.

### Authorization grant
Gives the app permission to retrieve an access token on behalf of the end user. OAuth 2.0 defines four specific "grant types".

### Access token
A long string of characters that serves as a credential used to access protected resources.

### Protected resource
Data owned by the resource owner. For example, the user's contact list, account information, or other sensitive data.

## Anonymous request
 yAPI supports anonymous request to some of the resources, for example you may list the countries available.

## Scopes
Scopes limit access for OAuth tokens providing a way to limit the amount of access that is granted to an access token.For example, an access token issued to a client app may be granted READ and WRITE access to protected resource as chat conversations or user profile data, or just READ. Scopes do not grant any additional permission beyond that which the user already has.


## Yalo OAuth protocol flows

### Resource owner grant type
The resource owner password grant type is used in our trusted internal applications.  In this configuration, the user provides his resource server credentials (username/password) to the client app, which sends them in the request, the server validates the credentials, and if they are valid, proceeds to generate an access token and returns it.

## Client credentials grant type

## Requirements to authenticate on Yalo platform
To authenticate through the OAuth2 server you need to provide:

1. Application client credentials that consist of a valid `clientId` and `clientSecret`.
2. Resource owner user credentials.
3. At least one scope to specify the type of access that are been requested.

## Signin a user through token generation [POST /oauth/token]
To signin a user you must generate a token that must be used in all the requests to the platform. This endpoint also has the ability of generating a chat session token if a `nonce` is provided or if a `chatSessionToken: true` paramed is added to the body.
To signup new a user you can use the same endpoint for user signing. The only difference will be the response code `201` recieved.

+ Parameters

     + Authorization: `Basic dG90bzplZHdhc2Fh` (String, optional) - Basic64 encode client credentials to be provided in the request header
     + username: `fabia@gmail.com` (String, required) - An email that represents the user to signin
     + password: `123` (String, required) - The user password
     + grantType: `password` (String, required) - The grant to be executed
     + nonce: `e7fzVtooU7U7Bx4HMliusVZVJj6VDkJaxrRi0yMN1mpcsmJCdDTtKUvBI02_0n_eahk9t9HIqLQ_ShLZ3IIBAQ` (String, optional) - Provide a nonce to also generate a chat session token.
     + chatToken: `true` (String, optional) - Provide this param if a nonce is not include and you want to get a chat session token.
     + Default: `false`

+ Request Signin a user (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "username": "fabia@gmail.com",
                "password":"1234",
                "grantType":"password"
            }

+ Response 200 (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "statusCode": 201,
                "user": {
                    "email": "fabia@yalochat.com"
                },
                "type": "bearer",
                "token": "c3d1973e5ca12eb80d5132283ebd850ede34ae17",
                "expiresIn": 3600,
                "refreshToken": "da0fc43d172ed901466dc783a75697e39bd7302f"
            }

+ Request Sign in a user with nonce an request a chat identity token (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "username": "fabia@gmail.com",
                "password":"1234",
                "grantType":"password",
                "nonce":"e7fzVtooU7U7Bx4HMliusVZVJj6VDkJaxrRi0yMN1mpcsmJCdDTtKUvBI02_0n_eahk9t9HIqLQ_ShLZ3IIBAQ"
            }

+ Response 200 (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "statusCode": 200,
                "user": {
                    "email": "fred@yalochat.com"
                },
                "type": "bearer",
                "token": "56f5ba105c3bc1cd132f91daee538011a2ccd6cb",
                "expiresIn": 3600,
                "chat": {
                    "identityToken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImN0eSI6ImxheWVyLWVpdDt2PTEiLCJraWQiOiJsYXllcjovLy9rZXlzL2ZhNjk3M2ZlLTY5NjUtMTFlNS1hODc3LWNlMjQwMjAwNTEyYSJ9.eyJpc3MiOiJsYXllcjovLy9wcm92aWRlcnMvYmVjODhmM2EtNjI2NS0xMWU1LWJjN2UtMGVkZmZlMDA3ODhmIiwicHJuIjoiZnJlZEBheWFsby5jbyIsImlhdCI6MTQ0ODEzMjk0NywiZXhwIjoxNDQ4MTQyOTQ3LCJuY2UiOiJ4NUpSMlNYTHZyZ0VrVjQxemtRUmN2SzYwVTFETTh4Nm02SHo4N2hQVU04aUYxZVo1QWpNV3Eta0ZiNzRwd0xoUHotTVRqWXhEbEVpazl3dEFDZlRNQSJ9.M61nHOa83wnCpFD14vqJPOU8TrglnsMb3M95R8KjSd2c0jHE9A9nNa_eahI0CvJ4SsvsMGxGwSyE94vFPNCxQTrmNb2jKnK4apQPQMs7_6jLArqps78kWI7IVFdXE-C8zRM3-jA3fJQiCCQeo9VFoD0SLrMFiiy3n23y3gZ4b04"
                }
            }    


+ Request Sign in a user with chat session token parameter true and nonce to get a `sessionToken` and `identityToken` (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "username": "fabia@gmail.com",
                "password":"1234",
                "grantType":"password",
                "nonce":"e7fzVtooU7U7Bx4HMliusVZVJj6VDkJaxrRi0yMN1mpcsmJCdDTtKUvBI02_0n_eahk9t9HIqLQ_ShLZ3IIBAQ",
                "chatSessionToken": true
            }

+ Response 200 (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "statusCode": 200,
                "user": {
                    "email": "fred@yalochat.com"
                },
                "type": "bearer",
                "token": "8fb3484d8b7f2dfaca53f653a605ec9cd9316723",
                "expiresIn": 3600,
                "chat": {
                    "sessionToken": "LPXXQXtj7eQpWw4GtSCsMYuTIf2pE6jLDGprScgor2z-VnrAkfJr577s0t4saaZM-z4f5Whq3S7tqAth4r_b5g.8-1",
                    "identityToken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImN0eSI6ImxheWVyLWVpdDt2PTEiLCJraWQiOiJsYXllcjovLy9rZXlzL2ZhNjk3M2ZlLTY5NjUtMTFlNS1hODc3LWNlMjQwMjAwNTEyYSJ9.eyJpc3MiOiJsYXllcjovLy9wcm92aWRlcnMvYmVjODhmM2EtNjI2NS0xMWU1LWJjN2UtMGVkZmZlMDA3ODhmIiwicHJuIjoiZnJlZEBheWFsby5jbyIsImlhdCI6MTQ0ODEzMzA1NiwiZXhwIjoxNDQ4MTQzMDU2LCJuY2UiOiJCaUthenBFaWN4UmZ3WFY3Y3FkU1VEeG0ybmFZbG9ycnQ2am05ZXd4MWRndFJUOHI1T0VYeERpeGxpYnEzV215Q3I4dzVRN1hUTVplT0tkaENMWFo0ZyJ9.Ngf5CqUxcAY5L8tuBAdbMmQKQck3vJZp3xPD2oTP90CjcVDPR-4KeIDqCILHhGfz_lAbxC3kjZ237EMxSuWYrZzKe0Gzxg5M-C-kTPXYk6HfulYYE6UTCQgNYSDmqa6VHWQi4y6T5ipIUcAhorCdRJyy8CbAQiyAebkcaZxYYQc"
                }
            }

+ Request Sign in a user with chat session token parameter without a nonce (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "username": "fabia@gmail.com",
                "password":"1234",
                "grantType":"password",
                "chatSessionToken": true
            }

+ Response 200 (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "user": {
                    "email": "fabia@yalochat.comm"
                },
                "tokenType": "bearer",
                "accessToken": "c3d1973e5ca12eb80d5132283ebd850ede34ae17",
                "expiresIn": 3600,
                "refreshToken": "da0fc43d172ed901466dc783a75697e39bd7302f"
                "chat":{
                    "sessionToken":"0bbKLunec_070Ma8_hRHFRUVpz2Bsp9Yz94yRd4EUs50LPBPndjxs5YG5loikeCpUp5WUSYPenUgMO7vPFKqBw.8-4",
                    "identityToken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImN0eSI6ImxheWVyLWVpdDt2PTEiLCJraWQiOiJsYXllcjovLy9rZXlzL2ZhNjk3M2ZlLTY5NjUtMTFlNS1hODc3LWNlMjQwMjAwNTEyYSJ9.eyJpc3MiOiJsYXllcjovLy9wcm92aWRlcnMvYmVjODhmM2EtNjI2NS0xMWU1LWJjN2UtMGVkZmZlMDA3ODhmIiwicHJuIjoiZnJlZEBheWFsby5jbyIsImlhdCI6MTQ0ODEzNDMzOCwiZXhwIjoxNDQ4MTQ0MzM4LCJuY2UiOiJ0OGdlVVRMQ1VURUxJemVwQlpTbnBxbjUzRVJwMnRvOTg1WHV6RGRuem9hcmNxbVQ3WHBTSUV0R3ZRaVExRy1vMUg3T0haTXFLZVhEV0xNdmpGeTVzQSJ9.Op_9K953ALli4YNliFqtukOCeajyCuhOaA3XIBqn2DGZx30z1xfwExkyS_pbaijBK48IxqV_YePkWi17MAaFlAmxYSgyKUOABUITN_bcFBVStd3gfUkjQbdxmeo45_rlS7MCUxTwnIZfE5hTgizvzCinOLhCMqHSaVr8ORJ9Yn0"
                }
            }

+ Request Singin with invalid password credentials (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "username": "fabia@gmail.com",
                "password":"invalidPassword",
                "grantType":"password",
                "chatSessionToken": true
            }

+ Response 401 (application/json)

    + Header

            WWW-Authenticate: Yalo Error type="user", code="invalidUserCredentials", error="User credentials are invalid"

    + Body

            {
                "statusCode": 401,
                "error": "Unauthorized",
                "message": "User credentials are invalid",
                "attributes": {
                    "type": "user",
                    "code": "invalidUserCredentials",
                    "error": "User credentials are invalid"
                }
            }

+ Request Sinup a new user (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "username": "fabia@gmail.com",
                "password":"1234",
                "grantType":"password"
            }

+ Response 201 (application/json)

    + Headers

            Authorization: Basic dG90bzplZHdhc2Fh

    + Body

            {
                "statusCode": 201,
                "user": {
                    "email": "fabia@yalochat.com",
                },
                "tokenType": "bearer",
                "accessToken": "c3d1973e5ca12eb80d5132283ebd850ede34ae17",
                "expiresIn": 3600,
                "refreshToken": "da0fc43d172ed901466dc783a75697e39bd7302f"
            }
