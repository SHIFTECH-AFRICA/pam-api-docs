## [PAM](https://pam.easyncpay.com/) API DOCS
* Welcome to [PAM](https://pam.easyncpay.com/) API,this api is organized around REST API. Our API has predictable resource-oriented URLs, accepts json/form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs that is GET and POST. You can invoke our API endpoints using REST clients like Postman or SoapUI and command line tools like curl and Node.js.

* The [SMSALES](https://pam.easyncpay.com/) API only accepts the Content-Type: application/json & Accept: application/json

### How To Get Started
* To make an API call, you will need to authenticate your app. We have provided an OAuth API for you to generate an access token, we support Authorization grant type. To authorize your API call to the OAuth API, you will need a Basic Auth over HTTPS authorization token.

#### Generating Access Token <span style="color:green"><kbd>GET</kbd></span>

```markdown
   https://api.smsales.co.ke/api/v1/token 
```

```json
var request = require('request');
var options = {
'method': 'GET',
'url': 'https://api.smsales.co.ke/api/v1/token',
    'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json',
    'Authorization': 'Basic ACCOUNT_API_TOKEN'
    }
}
```
```json
{
  "data": {
    "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczpcL1wvYXBpLnNtc2FsZXMuY28ua2VcL2FwaVwvdjFcL3Rva2VuIiwiaWF0IjoxNjIxOTY1OTk5LCJleHAiOjE2MjE5Njk1OTksIm5iZiI6MTYyMTk2NTk5OSwianRpIjoiNUlvc3NjdlRqZDU3bVdLcyIsInN1YiI6IjhiNWE5ZmEwLTM3ODYtNDRhOS05NmEwLWVlMTlmOTU2NDVjZiIsInBydiI6IjIzYmQ1Yzg5NDlmNjAwYWRiMzllNzAxYzQwMDg3MmRiN2E1OTc2ZjcifQ.mioHmrN-KJb8_rJd9FayfhBGI6G8Kg6g9nNg8c4GxjM",
    "TokenType": "Bearer",
    "Expires": 3600
  }
}
```

For more details see [Account Api Token](https://smsales.co.ke/profile).

#### Fetching Latest Sent Sms's <span style="color:green"><kbd>GET</kbd></span>
```markdown
   https://api.smsales.co.ke/api/v1/sms
```

```json
var request = require('request');
var options = {
'method': 'GET',
'url': 'https://api.smsales.co.ke/api/v1/sms',
    'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json',
    'Authorization': 'Bearer GIVE_THE_GENERATED_BEARER_TOKEN'
    }
}
```
#### Sending Bulk Sms <span style="color:red"><kbd>POST</kbd></span>
```markdown
   https://api.smsales.co.ke/api/v1/sms/send
```
*Params*
```json
{
  "api_sender" => "shiftech",// required check on your senderID's list for the API Sender
  "message" => "Hello Smsales.",// required
  "phone_numbers" => ["2547XXXXXXXX","2540XXXXXXXX","2547XXXXXXXX"],// required
  "scheduled_at" => "Y-m-d H:i:s", // optional
  "callback_url"=> "https://yourdomain/report"// optional this should be a POST request
}
```

```json
var request = require('request');
var options = {
'method': 'GET',
'url': 'https://api.smsales.co.ke/api/v1/sms/send',
    'headers': {
    'Content-Type': 'application/json',
    'Accept': 'application/json',
    'Authorization': 'Bearer GIVE_THE_GENERATED_BEARER_TOKEN'
    },
body: JSON.stringify({"api_sender":"shiftech","message":"Hello","phone_numbers":["2547XXXXXXXX","2540XXXXXXXX","2547XXXXXXXX"]})

}
```
```json
{
  "data": {
    "message": "Accepted for dispatch..."
  }
}
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
