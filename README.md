# Wanda.Exchange API v1 Docs

# Changes

# Base URL
Base URL is: https://api.wanda.exchange

# Endpoints
* [GET /v1/timestamp] (#v1-timestamp)
* [GET /v1/market/assets] (#v1-market-assets)
* [GET /v1/market/fiats] (#v1-market-fiats)
* [GET /v1/market/pairs] (#v1-market-pairs)
* [GET /v1/market/ticker] (#v1-market-ticker)
* [GET /v1/market/trades] (#v1-market-trades)
* [GET /v1/market/bids] (#v1-market-bids)
* [GET /v1/market/asks] (#get-market-asks)
* [GET /v1/market/open] (#get-market-open)
* [GET /v1/market/tv] (#get-market-tv)

* [POST /v1/user/wallets] (#post-user-wallets)
* [POST /v1/user/wallet] (#post-user-wallet)
* [POST /v1/user/bid/make] (#post-user-bid)
* [POST /v1/user/ask/make] (#post-user-ask)
* [POST /v1/user/order] (#post-user-order)

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

