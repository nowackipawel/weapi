# Wanda.Exchange API v1 Docs

# Changes

# Base URL
Base URL is: https://api.wanda.exchange

# Endpoints
* [GET /v1/timestamp] (#get-timestamp)
* [GET /v1/market/symbols] (#get-market-symbols)
* [GET /v1/market/ticker] (#get-market-ticker)
* [GET /v1/market/trades] (#get-market-trades)
* [GET /v1/market/bids] (#get-market-bids)
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


### GET /api/market/symbols

#### Description:
List all available fiat and asset symbols.

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
    },
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



