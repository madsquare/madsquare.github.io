# API

모든 API는 Header에 인증 정보를 추가하여 요청.

```
GET /api/verify HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

## Basic Token 생성

클라이언트 정보(id, secret)는 별도 관리자를 통해 발급.

### Samples

### NodeJS
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

```json
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

