# Verify

{% api-method method="post" host="" path="/users/verify/" %}
{% api-method-summary %}
Verify user account.
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to verify the email account of an user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
Token to verify an user account.
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User was sucessfuly verified.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "peter",
    "first_name": "Peter",
    "last_name": "Dinklage",
    "email": "peter@gmail.com",
    "phone_number": "+1 4564654648",
    "is_email_verified": true
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
There are errors with the given token.
{% endapi-method-response-example-description %}

```javascript
{
    "token": [
        "This field is required.",
        "Token is not valid"
    ],
    "non_field_errors": [
        "User is already verified."
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



