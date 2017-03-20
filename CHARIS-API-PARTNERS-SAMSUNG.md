# Samsung partners

## GET /v1/partners/samsung/celebs

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
profile_url | String | 프로필 이미지 URL
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
GET /v1/partners/samsung/celebs?page=1&limit=10 HTTP/1.1
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
      "uid": "USXXXXXX",
      "nickname": "Aiden Ahn",
      "country": "KR",
      "profile_url": "https://...",
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


## GET /v1/partners/samsung/contents

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
contents | Array[Contents] | 컨텐츠 목록

### Contents

Field | Type | Description
---|---|---
idx | Number | PK
thumb | String | 썸네일 URL
content | String | 영상 URL
title | String | 제목
comment | String | 코멘트

```
GET /v1/partners/samsung/contents?page=1&limit=10 HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

```javascript
{
  "page": 1,
  "limit": 10,
  "totalCount": 16,
  "totalPage": 2,
  "contents": [
    {
      "idx": 31,
      "thumb": "https://d3m7so2s2yecjy.cloudfront.net/reviews/thumb/201703_B15LL5Rqg.jpg",
      "content": "https://www.youtube.com/watch?v=O2YkW6EXvWU",
      "title": "Moisturizing Gel Mist by GLAMSKIN",
      "comment": "Always refreshing! Nutrient enriched gel type mist will calm down your skin \n\n\"The scent really wakes me up in the morning, and although it’s gel, it sprays out very fine mist. I spray before my makeup, and i use my hands to pat it in !\"- Mehgees\n\n↓ Click the link down below to find out more about Meghee's review!"
    },
  // ...
}
```
