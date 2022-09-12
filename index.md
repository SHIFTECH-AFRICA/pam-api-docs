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
#### Expected response:
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
#### Listing all your apps <span style="color:red"><kbd>Get </kbd></span>
```markdown
   https://pam.api.easyncpay.com/api/v1/app
```

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
*Params*
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
### expected response  *if the  Paybill/Till Number credentials are valid*

```
{
    "data": {
        "Message": "The m-pesa app keys are valid."
    },
    "success": true
}
```
### Register C2B callback <span style="color:RED"><kbd>POST</kbd></span>

```markdown
  https://pam.api.easyncpay.com/api/v1/m-pesa/c2b/register-url

```

```json
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://pam.api.easyncpay.com/api/v1/m-pesa/c2b/register-url',
  'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  },
  body: JSON.stringify({"Secret":""})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```
expected  response

```
{
    "data": {
        "Message": "Validation and Confirmation URLs are already registered"
    },
    "success": true
}
```
## STK PUSH 
<p>This section shows how to make stk push and callback data for both stk-push and lipa na mpesa.</p>

```markdown
https://pam.api.easyncpay.com/api/v1/m-pesa/c2b/stk-push

```
```json
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://pam.api.easyncpay.com/api/v1/m-pesa/c2b/stk-push',
  'headers': {
    'Accept': 'application/json',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({"CallingCode":"254","Secret":"","PhoneNumber":"","Amount":"1","ResultUrl":"","Description":"Testing the PAM API","TransactionType":"CustomerPayBillOnline/CustomerBuyGoodsOnline"})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```
#### STK paid expected  response

```json

"data": {
      "Success": true,
      "Description": "Transaction description.",
      "ReferenceNumber": "2BONOSBBTN",
      "PhoneNumber": "254XXXXXXXXX",
      "MpesaReceiptNumber": "PBO2ZOBY44",
      "Amount": 20000
}
```
### Expected response for a paid C2B

```json
"data": {
        "Success": true,
        "Description": "Transaction description.",
        "ReferenceNumber": "2BONOSBBTN",
        "PhoneNumber": "254XXXXXXXXX",
        "MpesaReceiptNumber": "PBO2ZOBY44",
        "Amount": 20000,
        'TransactionType': 'Pay Bill'
        'OrgAccountBalance': 50000
}
```
####  Expected response for a not paid STK
```json
"data": {
        "Success": false,
        "Description": "Request cancelled by user",
        "ReferenceNumber": "2BOXRDNMLU",
        "PhoneNumber": "254XXXXXXXXX"
}

```
### confirming stk payment<span style="color:green"><kbd>POST</kbd></span>
```markdown
  https://pam.api.easyncpay.com/api/v1/m-pesa/c2b/confirm-stk-payment

```

```json
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://pam.api.easyncpay.com/api/v1/m-pesa/c2b/confirm-stk-payment',
  'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  },
  body: JSON.stringify({"Secret":"", "ReferenceNumber":"", "ResultUrl":"",})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```
#### Expected response if the payment has been done
```json

"data": {
      "Success": true,
      "Description": "Transaction description.",
      "ReferenceNumber": "2BONOSBBTN",
      "PhoneNumber": "254XXXXXXXXX",
      "MpesaReceiptNumber": "PBO2ZOBY44",
      "Amount": 20000
}
```
#### Expected response if the payment has not been done

```json
"data": {
        "Success": false,
        "Description": "Request cancelled by user",
        "ReferenceNumber": "2BOXRDNMLU",
        "PhoneNumber": "254XXXXXXXXX"
}

```

### B2C <span> ( *business to customer* )</span><span style="color:RED"><kbd>POST</kbd></span> 
<p>This is where all the bulk payments are made.</p>

```markdown
https://pam.api.easyncpay.com/api/v1/m-pesa/b2c
```
```json
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://pam.api.easyncpay.com/api/v1/m-pesa/b2c',
  'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  },
  body: JSON.stringify({"CallingCode":"254","Secret":"","PhoneNumber":"","Amount":"10","ResultUrl":"","Description":"Testing the PAM API","TransactionType":"BusinessPayment/SalaryPayment/PromotionPayment"})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```
### Response for payment recieved through B2C  
```json

"data": {
       'Success' => true,
       'Description' => 'Salary payment',
       'ReferenceNumber' => '2BO6BCTLYF',
       'PhoneNumber' => '254XXXXXXXXX',
       'MpesaReceiptNumber' => 'PBO2ZOBY44',
       'Amount' => 50000,
       'B2CUtilityAccountAvailableFunds' => 70000,
       'B2CWorkingAccountAvailableFunds' => 70000,
       'B2CChargesPaidAccountAvailableFunds' => 70000
    }
```
### payment not received from B2C 

```json
"data": {
       "Success": false,
        "Description": "The initiator information is invalid.",
        "ReferenceNumber": "2BO6BCTLYF",
        "PhoneNumber": "254XXXXXXXXX"
}
```
### confirming B2C payment
confirming stk payment<span style="color:green"><kbd>POST</kbd></span>
```markdown
  https://pam.api.easyncpay.com/api/v1/m-pesa/b2c/confirm-withdraw

```

```json
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://pam.api.easyncpay.com/api/v1/m-pesa/b2c/confirm-withdraw',
  'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  },
  body: JSON.stringify({"Secret":"", "ReferenceNumber":"", "ResultUrl":"",})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```
#### Expected response if the payment has been made

```json

"data": {
       'Success' => true,
       'Description' => 'Salary payment',
       'ReferenceNumber' => '2BO6BCTLYF',
       'PhoneNumber' => '254XXXXXXXXX',
       'MpesaReceiptNumber' => 'PBO2ZOBY44',
       'Amount' => 50000,
       'B2CUtilityAccountAvailableFunds' => 70000,
       'B2CWorkingAccountAvailableFunds' => 70000,
       'B2CChargesPaidAccountAvailableFunds' => 70000
    }
```
##### Expected response if the payment has not been made
```json
"data": {
       "Success": false,
        "Description": "The initiator information is invalid.",
        "ReferenceNumber": "2BO6BCTLYF",
        "PhoneNumber": "254XXXXXXXXX"
}
```

## API libraries

Having trouble with API integration?. Check out our  [libraries](https://github.com/SHIFTECH-AFRICA/pam-php-sdk) for  a quick intergration, or [contact support](https://wa.me/message/UW2M6CP2ACOAF1) and we’ll help you sort it out.
 
