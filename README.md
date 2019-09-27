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
1529999999
```


### GET /api/market/assets

#### Description:
List all available assets.

#### Query:
* `ts` (int): Your timestamp

#### Response:
```javascript
{
  error: 0,
  result: [
    {
      id: 51,
      symbol: "BTC",
      name: "Bitcoin"
    },
    {
      id: 54,
      symbol: "ETH",
      name: "Etherium"
    }
  ]
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
  error: 0,
  result: [
    {
      id: 11,
      symbol: "THB",
      name: "Thai Bath"
    },
    {
      id: 12,
      symbol: "EUR",
      name: "Euro"
    }
  ]
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
  error: 0,
  result: [
    {
      id: 1,
      fiat: 11,
      asset: 51,
      pair: "THB_BTC"
    },
    {
      id: 3,
      fiat: 11,
      asset: 53,
      pair: "THB_ETH"
    }
  ]
}
```

