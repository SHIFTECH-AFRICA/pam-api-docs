## [PAM](https://pam.easyncpay.com/) API DOCS
* Welcome to [PAM](https://pam.easyncpay.com/) API,this api is organized around REST API. Our API has predictable resource-oriented URLs, accepts json/form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs that is GET and POST. You can invoke our API endpoints using REST clients like Postman or SoapUI and command line tools like curl and Node.js.

* The [PAM](https://pam.easyncpay.com/) API only accepts the Content-Type: application/json & Accept: application/json

### How To Get Started
* To make an API call, you will need to authenticate your app. We have provided an OAuth API for you to generate an access token, we support Authorization grant type. To authorize your API call to the OAuth API, you will need a Basic Auth over HTTPS authorization token.

#### Generating Access Token <span style="color:green"><kbd>GET</kbd></span>

```markdown
  https://pam.api.easyncpay.com/api/v1/token
```

```json
var request = require('request');
var options = {
   'method': 'GET',
   'url': 'https://pam.api.easyncpay.com/api/v1/token',
   'headers': {
       'Content-Type': 'application/json',
       'Accept': 'application/json',
       'Authorization': 'Basic ACCOUNT_API_TOKEN'
             }
       };
request(options, function (error, response) {
if (error) throw new Error(error);
   console.log(response.body);
});
```
```json
{
    "data": {
        "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczpcL1wvcGFtLmFwaS5lYXN5bmNwYXkuY29tXC9hcGlcL3YxXC90b2tlbiIsImlhdCI6MTYxNDU5NTI4MywiZXhwIjoxNjE0NTk4ODgzLCJuYmYiOjE2MTQ1OTUyODMsImp0aSI6IkYzVmpQNDJQb1ZjU0YycjIiLCJzdWIiOiI4OTczODllMy01ZjdjLTRhYjAtYjI2OS01YjFmNmI3NTM2NGEiLCJwcnYiOiI4N2UwYWYxZWY5ZmQxNTgxMmZkZWM5NzE1M2ExNGUwYjA0NzU0NmFhIn0.KWJbcAoIW6yF0IgCaylv7EqotDZnkXt5MvmuEZrjNbA",
        "TokenType": "Bearer",
        "Expires": 3600
    },
    "success": true
}
```

For more details see [Account Api Token](https://smsales.co.ke/profile).

#### listing your linked Paybill/Till numbers <span style="color:green"><kbd>GET</kbd></span>
```markdown
   https://pam.api.easyncpay.com/api/v1/shortcode
```

```json
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://pam.api.easyncpay.com/api/v1/shortcode',
  'headers': {
    'Accept': 'application/json',
    'Content-Type': 'application/json'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```
#### Listing all your apps <span style="color:red"><kbd>Get</kbd></span>
```markdown
   https://pam.api.easyncpay.com/api/v1/app
```
*Params*
```json
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://pam.api.easyncpay.com/api/v1/app',
  'headers': {
    'Accept': 'application/json'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```
#### Listing all your  latest transaction <span style="color:red"><kbd>Get</kbd></span>
```markdown
    https://pam.api.easyncpay.com/api/v1/pay-loads
```

```json
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://pam.api.easyncpay.com/api/v1/pay-loads',
  'headers': {
    'Accept': 'application/json'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```

### Validating Paybill/Till Number
<p>Provide all the valid information to check if the paybill/till number credentials are valid.</p><span style="color:green"><kbd>POST</kbd></span>

```markdown
  https://pam.api.easyncpay.com/api/v1/m-pesa/shortcode validate
```
##

```

```
```json
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://pam.api.easyncpay.com/api/v1/m-pesa/shortcode/validate',
  'headers': {
    'Accept': 'application/json',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({"ConsumerKey":"","ConsumerSecret":"","Environment":"sandbox/production"})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```
CallBack Results *if provided*.

```json
{
  "sent": true,
  "sender": "SHIFTECH", // Youe senderID
  "api_sender": "shiftech", // Your api sender
  "phone_number": "254XXXXXXXX",
  "batch": "1KTHKGKM8R",
  "account": {
    "sender_balance": 7000,
    "sms_balance": 13200
  }
}
```

## Support or Contact

Having trouble with API integration? Check out our [libraries](https://github.com/SHIFTECH-AFRICA/smsales-php-sdk) or [contact support](https://wa.me/message/UW2M6CP2ACOAF1) and we’ll help you sort it out.
