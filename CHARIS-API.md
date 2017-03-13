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

## GET /v1/celebs

### Parameter

Field | Type | Description
---|---|---
page | Number | 페이지 번호
limit | Number | 페이지 컨텐츠 수

### Response

Field | Type | Description
---|---|---
page | Number | 페이지 번호
limit | Number | 페이지 컨텐츠 수
totalCount | Number | 전체 컨텐츠 수
totalPage | Number | 총페이지 수
celebs | Array[Celeb] | 셀럽 목록

### Celeb

Field | Type | Description
---|---|---
uid | String | PK
nickname | String | 닉네임
country | String | 국가코드 (ISO 3166-1 alpha-2)
social_media | Array | 소셜미디어 정보

### Social Media
Field | Type | Description
---|---|---
type | String | `facebook`, `instagram`, `youtube`, `wechat`, `weibo`, `meipai`
url | String | 소셜미디어 URL
followers | Number | 소셜미디어 팔로워 수
engagement_rate | Number | Enagement Rate
video_engagement_rate | Number | Enagement Rate (비디오)

```
GET /v1/celebs?page=1&limit=10 HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

```javascript
{
  "page": 1,
  "limit": 10,
  "totalCount": 762,
  "totalPage": 77,
  "celebs": [
    {
      "nickname": "Aiden Ahn",
      "country": "KR",
      "social_media": [
        {
          "type": "facebook",
          "url": "https://www.facebook.com/facebook_url",
          "followers": 0,
          "engagement_rate": 0,
          "video_engagement_rate": 0
        },
        {
          "type": "instagram",
          "url": "https://www.instagram.com/instagram_url",
          "followers": 0,
          "engagement_rate": 0,
          "video_engagement_rate": 0
        }
      ]
    },
    // ...
    ```
