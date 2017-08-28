# Samsung partners

## GET /v1/partners/tving/banners

### Parameter

Field | Type | Description
---|---|---
platform | String | 노출 플랫폼 타입 (`APP`, `WEB`)
lang | String | 언어 코드 (ISO 639-1 Code, 현재 지원 가능 언어 코드. 기본설정 (`vi`))
country | String | 국가 코드 (ISO Alpha-2, 기본설정 (`VN`))

### Response

Field | Type | Description
---|---|---
banners | Array[Banner] | 배너 목록
platform | String | 노출 플랫폼 타입
lang | String | 언어 코드
country | String | 국가 코드

### Banner

Field | Type | Description
---|---|---
image | String | 이미지 URL
link | String | 배너 링크 URL


```
GET /v1/partners/tving/banners?platform=WEB&lang=vi&country=VN HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

```javascript
{
    "banners": [
        {
            "image": "https://img.hicharis.net/unsafe/600x100/https%3A%2F%2Fd3m7so2s2yecjy.cloudfront.net%2Fmain%2Ftving%2Fvi%2F201708_HJewf5IZKW.jpg",
            "link": "https://hicharis.net/tving"
        },
        {
            "image": "https://img.hicharis.net/unsafe/600x100/https%3A%2F%2Fd3m7so2s2yecjy.cloudfront.net%2Fmain%2Ftving%2Fvi%2F201708_BJl3GcLbtZ.jpg",
            "link": "https://hicharis.net/tving"
        }
    ],
    "platform": "WEB",
    "lang": "vi",
    "country": "VN"
}
```
