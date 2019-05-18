# Read, Update & Delete

{% api-method method="get" host="" path="/users/:username/" %}
{% api-method-summary %}
Get User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve an user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
Username of the user to get.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Json Web Token to login to the api.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User exists and you retrieved it sucessfuly.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "cheke",
    "first_name": "lkasjdljaslkjasd",
    "last_name": "Banos Ramirez",
    "email": "chekelosos@gmail.com",
    "phone_number": "+52 9581006329",
    "is_email_verified": false
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Authentication credentials are not valid.
{% endapi-method-response-example-description %}

```javascript
// Different responses.
{
    "detail": "Authentication credentials were not provided.",
}
{
    "detail": "Given token not valid for any token type",
    "code": "token_not_valid",
    "messages": [
        {
            "token_class": "AccessToken",
            "token_type": "access",
            "message": "Token is invalid or expired"
        }
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
You are not the account owner.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "You are not the account owner."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Users does not exists.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "Not found."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="" path="/users/:username/" %}
{% api-method-summary %}
Update User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to update an user
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
Username of the user to get.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Json Web Token to login to the api.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="refresh\_token" type="string" required=false %}
Actual refresh token to blacklist it if the password is sucessfuly changed.
{% endapi-method-parameter %}

{% api-method-parameter name="new\_password\_confirmation" type="string" required=false %}
Confirmation of the user new password
{% endapi-method-parameter %}

{% api-method-parameter name="new\_password" type="string" required=false %}
User new password.
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
User actual password.
{% endapi-method-parameter %}

{% api-method-parameter name="phone\_number" type="string" required=false %}
User phone number.
{% endapi-method-parameter %}

{% api-method-parameter name="last\_name" type="string" required=false %}
User last name.
{% endapi-method-parameter %}

{% api-method-parameter name="first\_name" type="string" required=false %}
User first name.
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=true %}
User nickname
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User was sucessfuly updated.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "cheke",
    "first_name": "lkasjdljaslkjasd",
    "last_name": "Banos Ramirez",
    "email": "chekelosos@gmail.com",
    "phone_number": "+52 9581006329",
    "is_email_verified": false
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Given data is incorrect or data is missing. Examples:
{% endapi-method-response-example-description %}

```javascript
{
    "refresh_token": [
        "Token is blacklisted",
        "Token is invalid or expired"
    ],    
    "username": [
        "This field is required.",
        "A user with that username already exists."
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Invalid authentication credentials.
{% endapi-method-response-example-description %}

```javascript
// Different responses.
{
    "detail": "Authentication credentials were not provided.",
}
{
    "detail": "Given token not valid for any token type",
    "code": "token_not_valid",
    "messages": [
        {
            "token_class": "AccessToken",
            "token_type": "access",
            "message": "Token is invalid or expired"
        }
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
The user you request to update is not the same as the requesting user.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "You are not the account owner."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
User could not be found.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "Not found."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
The refresh token will be blacklisted that you provided will be blacklisted, so you will need to get a new one using login endpoint.
{% endhint %}

{% api-method method="patch" host="" path="/users/:username/" %}
{% api-method-summary %}
Partial Update User
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
Username of the user to get.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Json Web Token to login to the api.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="username" type="string" required=false %}
User nickname.
{% endapi-method-parameter %}

{% api-method-parameter name="last\_name" type="string" required=false %}
User last name
{% endapi-method-parameter %}

{% api-method-parameter name="first\_name" type="string" required=false %}
User first name
{% endapi-method-parameter %}

{% api-method-parameter name="phone\_number" type="string" required=false %}
User phone number
{% endapi-method-parameter %}

{% api-method-parameter name="refresh\_token" type="string" required=false %}
Actual refresh token to blacklist it if the password is sucessfuly changed.
{% endapi-method-parameter %}

{% api-method-parameter name="new\_password\_confirmation" type="string" required=false %}
Confirmation of the new password
{% endapi-method-parameter %}

{% api-method-parameter name="new\_password" type="string" required=false %}
User new password
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
User actual password
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User was successfuly updated.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "cheke",
    "first_name": "lkasjdljaslkjasd",
    "last_name": "Banos Ramirez",
    "email": "chekelosos@gmail.com",
    "phone_number": "+52 9581006329",
    "is_email_verified": false
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Given data is incorrect or data  is missing. Examples:
{% endapi-method-response-example-description %}

```javascript
{
    "refresh_token": [
        "Token is blacklisted",
        "Token is invalid or expired"
    ],    
    "username": [
        "This field is required.",
        "A user with that username already exists."
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Invalid authentication credentials.
{% endapi-method-response-example-description %}

```javascript
// Different responses.
{
    "detail": "Authentication credentials were not provided.",
}
{
    "detail": "Given token not valid for any token type",
    "code": "token_not_valid",
    "messages": [
        {
            "token_class": "AccessToken",
            "token_type": "access",
            "message": "Token is invalid or expired"
        }
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
The user you request to update is not the same as the requesting user.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "You are not the account owner."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
User could not be found.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "Not found."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="" path="/users/:user/" %}
{% api-method-summary %}
Delete user
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to delete an user account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
Username of the user to get.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Json Web Token to login to the api.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
User was deleted successfuly.
{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Invalid credentials.
{% endapi-method-response-example-description %}

```javascript
// Different responses.
{
    "detail": "Authentication credentials were not provided.",
}
{
    "detail": "Given token not valid for any token type",
    "code": "token_not_valid",
    "messages": [
        {
            "token_class": "AccessToken",
            "token_type": "access",
            "message": "Token is invalid or expired"
        }
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
The user you requested to delete is not the same as the requesting user.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "You are not the account owner."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
User you request to delete does not exists.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "Not found."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

