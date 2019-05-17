# Signup

{% api-method method="post" host="" path="/users/signup/" %}
{% api-method-summary %}
Create User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to create a new user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="last\_name" type="string" required=true %}
User last name
{% endapi-method-parameter %}

{% api-method-parameter name="first\_name" type="string" required=true %}
User first name.
{% endapi-method-parameter %}

{% api-method-parameter name="password\_confirmation" type="string" required=true %}
It will be used to confirm that the given password has no errors, so the user could login successfuly after this\(Should be the same as the password\)G
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
Password it will be used to login.
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
User email.
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=true %}
User nickname.UI  
  
U{
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
User sucessfuly created
{% endapi-method-response-example-description %}

```javascript
{
    "username": "peter",
    "first_name": "Peter",
    "last_name": "Newman",
    "email": "peterinthespace@gmail.com",
    "phone_number": "+1 54465134564",
    "is_email_verified": false
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The data you give is wrong, here are listed some of the most common errors.
{% endapi-method-response-example-description %}

```javascript
{
    "username": [
        "This field is required.",
        "Ensure this field has no more than 150 characters.",
        "Ensure this field has at least 2 characters."
    ],
    "email": [
        "This field is required.",
        "Enter a valid email address.",
        "Ensure this field has no more than 1000 characters.",
        "Ensure this field has at least 6 characters."
    ],
    "password": [
        "This field is required.",
        "Ensure this field has at least 8 characters"
    ],
    "password_confirmation": [
        "This field is required.",
        "Ensure this field has at least 8 characters"
    ],
    "phone_number": [
        "This field is required.",
        "Phone number must be entered in the format: +99 999. Up to 20 digits allowed."
    ],
    "first_name": [
        "This field is required."
    ],
    "last_name": [
        "This field is required."
    ],
    "non_field_errors": [
        "This password is too common.",
        "This password is entirely numeric."
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

