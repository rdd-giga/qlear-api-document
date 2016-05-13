# Introduction
> To access api, use the access token, assigned by QLEAR:

Welcome to the QLEAR API! You can use our API to access QLEAR API endpoints, which can get all informations about user, location, monitor and reading data etc.

# Access Token


```ruby
content = RestClient.get 'https://example.com/v2/ping',
  {params: {access_token: '12345'}}
```

> The above returns JSON structured like this:

```json
{
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

QLEAR uses access token to allow access to the API. you can contact QLEAR support to obtain the token.

QLEAR expects for the access token to be included in all API requests to the server in the query string.

# Localization

QLEAR API supports localization for error messages and other strings. Localization is defined in each request with query string 'locale'. Accepted values are currently:

* en    - English (default)
* zh-CN - Chinese

Numbers, currency and datetime don’t rely on localization so they will always be returned in standard format.