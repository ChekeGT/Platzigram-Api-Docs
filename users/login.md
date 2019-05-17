# Login

{% api-method method="post" host="" path="/users/login/" %}
{% api-method-summary %}
Get JWT for login
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to login to platzigram api using Json Web Tokens.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="username" type="string" required=false %}
Username to login
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
Password to login
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
You have login successfuly.
{% endapi-method-response-example-description %}

```javascript
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU1ODIwOTI1NiwianRpIjoiZjdiMThmYjJmNmU0NGNkN2JjMDJkMGIxNjI1MThhOWYiLCJ1c2VyX2lkIjo1fQ.iUgCKzdOFm91i_ZcvrsrsbnM41jXvHdoqzwFHkfzgsI",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTU4MTIzMDM2LCJqdGkiOiIyZjRiYTQ2OWM4YmY0NGZhYmVkODA1YzRkNDNmZDJkYiIsInVzZXJfaWQiOjV9.-AHMk8aTOMMyxOtZjKGQ-TH5nIq72cTwoMH0O0YVncM"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Data is missing
{% endapi-method-response-example-description %}

```javascript
{
    "username": [
        "This field is required."
    ],
    "password": [
        "This field is required."
    ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Invalid credentials.
{% endapi-method-response-example-description %}

```javascript
{
    "detail": "No active account found with the given credentials"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
If you want to login "access" token needs to be in Authorization Header after word "JWT" in this way "JWT {token}".
{% endhint %}

{% hint style="warning" %}
Access token lifetime is of 5 minutes; after that you will ned to use the refresh endpoint to get a new access token.
{% endhint %}

{% page-ref page="refresh-access-token.md" %}

