# Wanda.Exchange API v1 Docs

# Changes

# Base URL
Base URL is: https://api.wanda.exchange

## Additional information
* All dates: UTC
* 

# Endpoints
* [GET /v1/timestamp] (#get-v1timestamp)
* [GET /v1/market/assets] (#get-v1market-assets)
* [GET /v1/market/fiats] (#get-v1marketfiats)
* [GET /v1/market/pairs] (#get-v1marketpairs)
* [GET /v1/market/ticker] (#get-v1marketticker)
* [GET /v1/market/trades] (#get-v1markettrades)
* [GET /v1/market/bids] (#get-v1marketbids)
* [GET /v1/market/asks] (#get-v1marketasks)
* [GET /v1/market/open] (#get-v1marketopen)
* [GET /v1/market/tv] (#get-v1markettv)

* [POST /v1/user/wallets] (#post-v1userwallets)
* [POST /v1/user/wallet] (#post-v1userwallet)
* [POST /v1/user/bid/make] (#post-v1userbid)
* [POST /v1/user/ask/make] (#post-v1userask)
* [POST /v1/user/order] (#post-v1userorder)

# Constructing requests
## Request Header
Authentication requires API KEY and API SECRET. 
Every request must contain following headers:
* Accept: application/json
* Content-Type: application/json
* X-WEX-APIKEY: {API KEY}

## Payload
Payload format is always a JSON. Every payload must contain timestamp (`ts`) and for user specified data signature key (`sig`) is required.


### Example payload with out signature:
```javascript
{"from":"THB","to":"LTC","amount":34.012,"rate":123.456,"type":"market","ts":1567890123}
```
### Example payloadWith signature:
```javascript
{"from":"THB","to":"LTC","amount":34.012,"rate":123.456,"type":"market","ts":1567890123,"sig":"1e5ffc1dc3b5547950bb017133add50e"}
```
Signature must equal to result of contatation of: `ts` and your {API KEY}. If your {API KEY} equals: XYZ your signature should be like in the example above.


# API documentation
Refer to the following for description of each endpoint

### GET /v1/timestamp

#### Description:
Get the server timestamp.

#### Query:
* `ts` (int): Your timestamp

#### Response:
```javascript
{
  error: false,
  result: 1567890123
}
```


### GET /api/market/assets

#### Description:
List all available assets.

#### Query:
* `ts` (int): Your timestamp

#### Response:
```javascript
{
    "result": [
        {
            "id": 51,
            "symbol": "BTC",
            "name": "Bitcoin"
        },
        {
            "id": 52,
            "symbol": "BCH",
            "name": "Bitcoin Cash"
        },
        {
            "id": 53,
            "symbol": "BTG",
            "name": "Bitcoin Gold"
        },
        {
            "id": 54,
            "symbol": "ETH",
            "name": "Ethereum"
        },
        {
            "id": 55,
            "symbol": "LTC",
            "name": "Litecoin"
        },
        {
            "id": 56,
            "symbol": "XLM",
            "name": "Stellar Lumens Coin"
        },
        {
            "id": 57,
            "symbol": "XRP",
            "name": "Ripple"
        },
        {
            "id": 58,
            "symbol": "ZEC",
            "name": "Zcash"
        },
        {
            "id": 59,
            "symbol": "DASH",
            "name": "Dash"
        }
    ],
    "error": false
}
```


### GET /api/market/fiats

#### Description:
List all available fiats.

#### Query:
* `ts` (int): Your timestamp

#### Response:
```javascript
{
    "result": [
        {
            "id": 11,
            "symbol": "THB",
            "name": "Thai Bat"
        },
        {
            "id": 13,
            "symbol": "EUR",
            "name": "Euro"
        }
    ],
    "error": false
}
```


### GET /api/market/pairs

#### Description:
List all available pairs (fiat -> asset).

#### Query:
* `ts` (int): Your timestamp

#### Response:
```javascript
{
    "result": [
        {
            "id": 1,
            "from": "THB",
            "to": "BTC",
            "pair": "THB_BTC",
            "availability": {
                "asks": true,
                "bids": true
            }
        },
        {
            "id": 2,
            "from": "THB",
            "to": "BCH",
            "pair": "THB_BCH",
            "availability": {
                "asks": true,
                "bids": true
            }
        },
        {
            "id": 3,
            "from": "THB",
            "to": "ETH",
            "pair": "THB_ETH",
            "availability": {
                "asks": true,
                "bids": true
            }
        },
        {
            "id": 4,
            "from": "THB",
            "to": "LTC",
            "pair": "THB_LTC",
            "availability": {
                "asks": true,
                "bids": true
            }
        },
        {
            "id": 5,
            "from": "THB",
            "to": "XRP",
            "pair": "THB_XRP",
            "availability": {
                "asks": true,
                "bids": true
            }
        },
        {
            "id": 6,
            "from": "THB",
            "to": "DASH",
            "pair": "THB_DASH",
            "availability": {
                "asks": true,
                "bids": true
            }
        }
    ],
    "error": false
}
```

```
{
  "id": 6, // ID
  "from": "THB", // Asset (fiat) from
  "to": "DASH", // Asset (cryptocurrency) to
  "pair": "THB_DASH", // Pair name
  "availability": {
    "asks": true, // Availability of placing asks
    "bids": true  // Availability of placing asks
  }
}
```



### GET /v1/market/ticker

#### Description:
Get ticker information.

#### Query:
* `ts` (int): Your timestamp
* `sym` (string) The symbol (optional)

#### Response:
```javascript
{
  THB_BTC: {
    id: 1,
    last: "216415.00",
    lowestAsk: "216678.00",
    highestBid: "215000.00",
    percentChange: "1.91",
    baseVolume: "71.02603946",
    quoteVolume: "15302897.99",
    isFrozen: "0",
    high24hr: "221396.00",
    low24hr: "206414.00"
  },
  THB_ETH: {
    id: 2,
    last: "11878.00",
    lowestAsk: "12077.00",
    highestBid: "11893.00",
    percentChange: "-0.49",
    baseVolume: "455.17839270",
    quoteVolume: "5505664.42",
    isFrozen: "0",
    high24hr: "12396.00",
    low24hr: "11645.00"
  }
}
```



# Errors
## API Calls
### No API Key in HTTP Request Headers
Status code: 400
```javascript
{
  "result": null,
  "error": {
    "id": 10,
    "name": "APIKEY_HEADER_HAS_NOT_BEEN_PROVIDED",
    "description": "ApiV1.error_APIKEY_HEADER_HAS_NOT_BEEN_PROVIDED",
    "params": []
  }
}
```

### API Key does not exist
Status code: 401
```javascript
{
  "result": null,
  "error": {
    "id": 11,
    "name": "APIKEY_CANNOT_BE_VERIFIED",
    "description": "ApiV1.error_APIKEY_CANNOT_BE_VERIFIED",
    "params": []
  }
}
```

### API KEY has been deleted
Status code: 403
_Plase note: `params` key could be unavailable._
```javascript
{
  "result": null,
  "error": {
    "id": 15,
    "name": "APIKEY_HAS_BEEN_DELETED",
    "description": "API KEY has been deleted at: Saturday, September 29, 2018 8:19:27 AM UTC",
    "params": [
      {
        "date": "2019-09-29 08:19:27.000000",
        "timezone_type": 3,
        "timezone": "UTC"
      }
    ]
  }
}
```



### API KEY has been expired
Status code: 403
_Plase note: `params` key could be unavailable._
```javascript
{
  "result": null,
  "error": {
    "id": 12,
    "name": "APIKEY_HAS_BEEN_EXPIRED",
    "description": "API KEY has been expired at: Saturday, September 29, 2018 11:05:48 AM UTC",
    "params": [
      {
        "date": "2019-09-29 11:05:48.000000",
        "timezone_type": 3,
        "timezone": "UTC"
      }
    ]
  }
}
```
