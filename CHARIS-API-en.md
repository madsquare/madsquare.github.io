# API

All APIs should be requested by adding authentication information to the header.

```
GET /api/verify HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

## Creating a Basic Token

The client information (id, secret) is issued by the administrator.

### Samples

#### NodeJS
```javascript
var endpoint = 'https://api.hicharis.net'
var client = {
  id: '__CLIENT_ID__',
  secret: '__CLIENT_SECRET__'
}

var ts = Date.now()
var secret = md5(client.secret + ts)
var token = new Buffer([client.id, secret, ts].join(':')).toString('base64')

request({
  url: endpoint + '/api/verify',
  headers: {
    Authorization: 'Basic ' + token
  }
}, function (err, res, body) {
  console.log(body)
})
```

#### Javascript
```javascript
var endpoint = 'https://api.hicharis.net'
var client = {
  id: '__CLIENT_ID__',
  secret: '__CLIENT_SECRET__'
}

var ts = Date.now()
var secret = CryptoJS.MD5(client.secret + ts)
var token = CryptoJS.enc.Base64.stringify(
    CryptoJS.enc.Utf8.parse([client.id, secret, ts].join(':'))
)

$.ajax({
  url: endpoint + '/api/verify',
  headers: {
    Authorization: 'Basic ' + token
  },
  success: function (res) {
    console.log(res)
  }
})
```

#### Response
```javascript
// success
{
  "results": {
    "client": {
      "clientId": "__CLIENT_ID__"
    }
  }
}

// error
{
  "code": "auth.required_authorization",
  "status": 403,
  "message": "There no authorization data.",
  "extra": {
    
  }
}
```

