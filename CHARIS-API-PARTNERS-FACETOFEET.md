# Facetofeet partners

## GET /v1/partners/facetofeet/categories

Load category list

### Parameter

Field | Type | Description | Default
---|---|---|---
lang | String | Language code | `en`

* [ISO 639-1 Codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
* Supported Language Codes: `en`, `ko`, `th`, `id`, `ms`, `vi`, `zh-TW`, `zh-CN`,

### Response

Field | Type | Description
---|---|---
categories | Array[CATEGORY] | Category list

#### CATEGORY

Field | Type | Description
---|---|---
sku | String | SKU
lang | String | Language code
name | String | Name
children | String | Sub category list

```
GET /v1/partners/facetofeet/categories?lang=en HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

```javascript
{
  "categories": [
    {
      "sku": "CAHJEGQMOS",
      "lang": "en",
      "name": "MAKEUP",
      "children": [
        {
          "sku": "CASJPO5L6S",
          "lang": "en",
          "name": "FACE"
        },
        // ...
      ]
    }
  }
}
```


## GET /v1/partners/facetofeet/saelgoods

Search salegoods list

### Parameter

Field | Type | Description | Default
---|---|---|---
page | Number | Number of page | 1
limit | Number | Number of results returned | 10
lang | String | Language code | `en`
currency | String | Currency code | `USD`
filter | Object | Filter of results returned
[filter.seller_id] | Array | List of seller's `uid`
[filter.category] | String | Category `sku`
[filter.url] | Array | List of sale item's `url`

* Supported Currency Codes : `USD`, `KRW`, `THB`, `IDR`, `MYR`, `VND`, `PHP`, `SGD`, `TWD`, `CNY`

### Response

Field | Type | Description
---|---|---
result.page | Number | Number of page
result.limit | Number | Number of results returned
result.totalCount | Number | Total number of search result values
result.totalPage | Number | Total number of pages
result.saleGoods | Array[SALEGOODS] | Search results of sale items

#### SALEGOODS
Field | Type | Description
---|---|---
sku | String | SKU
currency | String | Currency code
fixed_price | Number | Price before discount
price | Number | Actual selling price
discount_rate | Number | Discount rate
thumb_img | String | Thumbnail image url
meta | Object | Meta Data
meta.name | String | Name of sales item
meta.brand | String | Brand name
url | String | Details page url for sales item
shipping_supply | String | Shipping support type (`free`, `half`, null)
seller | Object | Seller data
seller.uid | String | Seller's `uid`
seller.nickname | String | Nickname
seller.url | String | Shop url
seller.profile_img | String | Profile image url

##### Search by url
```
GET /v1/partners/facetofeet/salegoods?page=1&limit=10&filter={"url":["https://hicharis.net/charis/aG"]} HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```
```javascript
{
    "result": {
        "page": 1,
        "limit": 10,
        "totalCount": 1,
        "totalPage": 1,
        "saleGoods": [
            {
                "sku": "SG95031315S12MRCKe",
                "currency": "USD",
                "fixed_price": 29.99,
                "price": 28.49,
                "discount_rate": 6,
                "thumb_img": "https://img.hicharis.net/unsafe/165x165/http%3A%2F%2Fd3m7so2s2yecjy.cloudfront.net%2Fproducts%2FP91552695HJ1at6Val%2F201704_BJneGdSpe.jpg",
                "meta": {
                    "name": "Official - Pocket Mini Flat Iron",
                    "brand": "VODANA"
                },
                "url": "https://hicharis.net/charis/aG",
                "shipping_supply": "free",
                "seller": {
                    "uid": "US57933191Ekdo9EkTx",
                    "nickname": "Charis",
                    "url": "https://hicharis.net/charis",
                    "profile_img": "https://img.hicharis.net/unsafe/126x126/http%3A%2F%2Fs3.ap-northeast-2.amazonaws.com%2Fbeta.charis.img%2Fusers%2FUS57933191Ekdo9EkTx%2F201706_SyMndDiImZ.jpeg"
                }
            }
        ]
    }
}
```

##### Search by category, seller
```
GET /v1/partners/facetofeet/salegoods?page=1&limit=10&filter={"category":"CARYDB2OQI","seller_id":["US57933191Ekdo9EkTx"]} HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

```javascript
{
  "result": {
    "page": 1,
    "limit": 10,
    "totalCount": 2,
    "totalPage": 1,
    "saleGoods": [
      {
        "sku": "SG64230651E1jMfUJQ-",
        "currency": "USD",
        "fixed_price": 22.91,
        "price": 18.33,
        "discount_rate": 20,
        "thumb_img": "https://img.hicharis.net/unsafe/165x165/http%3A%2F%2Fs3.ap-northeast-2.amazonaws.com%2Fbeta.charis.img%2Fproducts%2FP64199298EJQjw0RMb%2Fthumbnail_glamskin_mist.jpg",
        "meta": {
          "name": "PAPAYA & GRAPEFRUIT MOISTURIZING GEL MIST",
          "brand": "Glamskin"
        },
        "url": "https://hicharis.net/charis/3u",
        "shipping_supply": "free",
        "seller": {
          "uid": "US57933191Ekdo9EkTx",
          "nickname": "Charis",
          "url": "https://hicharis.net/charis",
          "profile_img": "https://img.hicharis.net/unsafe/126x126/http%3A%2F%2Fs3.ap-northeast-2.amazonaws.com%2Fbeta.charis.img%2Fusers%2FUS57933191Ekdo9EkTx%2F201706_SyMndDiImZ.jpeg"
        }
      },
      {
        "sku": "SG62847038N1kPrN5-b",
        "currency": "USD",
        "fixed_price": 76.36,
        "price": 61.09,
        "discount_rate": 20,
        "thumb_img": "https://img.hicharis.net/unsafe/165x165/http%3A%2F%2Fs3.ap-northeast-2.amazonaws.com%2Fbeta.charis.img%2Fabelrouge%2Fcream%2Fbasic_01.jpg",
        "meta": {
          "name": "Aqua Miracle Cream",
          "brand": "Abelrouge"
        },
        "url": "https://hicharis.net/charis/1S",
        "shipping_supply": "free",
        "seller": {
          "uid": "US57933191Ekdo9EkTx",
          "nickname": "Charis",
          "url": "https://hicharis.net/charis",
          "profile_img": "https://img.hicharis.net/unsafe/126x126/http%3A%2F%2Fs3.ap-northeast-2.amazonaws.com%2Fbeta.charis.img%2Fusers%2FUS57933191Ekdo9EkTx%2F201706_SyMndDiImZ.jpeg"
        }
      }
    ]
  }
}
```

## GET /v1/partners/facetofeet/salegoods/search?filter={"keyword":""}

Search salegoods by keyword

### Parameter

Field | Type | Description | Default
---|---|---|---
page | Number | Number of page | 1
limit | Number | Number of results returned | 10
lang | String | Language code | `en`
currency | String | Currency code | `USD`
keyword | String | Search Keyword | 

* Supported Currency Codes : `USD`, `KRW`, `THB`, `IDR`, `MYR`, `VND`, `PHP`, `SGD`, `TWD`, `CNY`

### Response

Field | Type | Description
---|---|---
result.page | Number | Number of page
result.limit | Number | Number of results returned
result.totalCount | Number | Total number of search result values
result.totalPage | Number | Total number of pages
result.list | Array[SALEGOODS] | Search results of sale items

#### SALEGOODS
Field | Type | Description
---|---|---
sku | String | SKU
currency | String | Currency code
fixed_price | Number | Price before discount
price | Number | Actual selling price
discount_rate | Number | Discount rate
thumb_img | String | Thumbnail image url
meta | Object | Meta Data
meta.name | String | Name of sales item
meta.brand | String | Brand name
url | String | Details page url for sales item
shipping_supply | String | Shipping support type (`free`, `half`, null)
seller | Object | Seller data
seller.uid | String | Seller's `uid`
seller.nickname | String | Nickname
seller.url | String | Shop url
seller.profile_img | String | Profile image url

##### Search API
```
GET /v1/partners/facetofeet/salegoods/search?page=1&limit=10 HTTP/1.1
Host: api.hicharis.net
Content-Type: application/json
Authorization: Basic __BASIC_TOKEN__
```

```javascript
{
  "searchModel": {
    "page": 1,
    "limit": 10,
    "totalCount": 2,
    "totalPage": 1,
    "list": [
      {
        "sku": "SG17738B19EYSWVQB1",
        "currency": "USD",
        "fixed_price": 18.99,
        "price": 12.99,
        "discount_rate": 32,
        "thumb_img": "https://img.hicharis.net/unsafe/165x165/http%3A%2F%2Fs3.ap-southeast-1.amazonaws.com%2Fprd.charis.img%2Fproducts%2FP17561HJHENLPRMB1X%2F201801_ryelDVTaBz.jpg",
        "meta": {
          "name": "[Romand]CREAMY LIPSTICK",
          "brand": "Facetofeet"
        },
        "url": "https://hicharis.net/facetofeet/9b6",
        "shipping_supply": null,
        "seller": {
          "uid": "US17637RY1T4AW2GBJ",
          "nickname": "facetofeet",
          "url": "https://hicharis.net/facetofeet",
          "profile_img": "https://img.hicharis.net/unsafe/126x126/http%3A%2F%2Fs3.ap-southeast-1.amazonaws.com%2Fprd.charis.img%2Fusers%2FUS17637RY1T4AW2GBJ%2F201804_rJgXNRyX2f.png"
        }
      },
      {
        "sku": "SG17738BKSFESWE7HY",
        "currency": "USD",
        "fixed_price": 13.74,
        "price": 10.99,
        "discount_rate": 21,
        "thumb_img": "https://img.hicharis.net/unsafe/165x165/http%3A%2F%2Fs3.ap-southeast-1.amazonaws.com%2Fprd.charis.img%2Fproducts%2FP17707B1TVCGCQH1GY%2F201806_SJlYZ8NfMm.jpg",
        "meta": {
          "name": "Romand Zerogram Matt Lipstick",
          "brand": "Facetofeet"
        },
        "url": "https://hicharis.net/facetofeet/9b8",
        "shipping_supply": null,
        "seller": {
          "uid": "US17637RY1T4AW2GBJ",
          "nickname": "facetofeet",
          "url": "https://hicharis.net/facetofeet",
          "profile_img": "https://img.hicharis.net/unsafe/126x126/http%3A%2F%2Fs3.ap-southeast-1.amazonaws.com%2Fprd.charis.img%2Fusers%2FUS17637RY1T4AW2GBJ%2F201804_rJgXNRyX2f.png"
        }
      }
    ]
  }
}
```
