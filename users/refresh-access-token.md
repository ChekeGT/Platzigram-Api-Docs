# Refresh Access Token

{% api-method method="post" host="" path="/users/refresh-token/" %}
{% api-method-summary %}
Refresh  Access token
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get a new access token using your refresh token.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="refresh" type="string" required=true %}
Refresh JWT
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The new access token was given to you.
{% endapi-method-response-example-description %}

```javascript
{
	"refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU1ODIxMTAzMCwianRpIjoiNjAxMmMxOTVkN2JjNGE3YjhiZWFjNzYwNTQ3YWJkMjUiLCJ1c2VyX2lkIjo1fQ.8pzXH30TjNhCWwSmPKg-x0b55uNB5Zp2Pe1VD61kpzU"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
There are errors with the given data. They could be:
{% endapi-method-response-example-description %}

```javascript
{
    "refresh": [
        "This field is required."
    ]
    "non_field_errors": [
        "User is already verified."
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Refresh token is invalid.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "Token is invalid or expired",
    "code": "token_not_valid"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
Refresh token lifetime is of 24 hours after that you will need to ask the user for their credentials again.
{% endhint %}

