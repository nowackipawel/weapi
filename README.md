# Wanda.Exchange API v1 Docs

# Changes

# Base URL
Base URL is: https://api.wanda.exchange

## Additional information
* All dates: UTC


# Endpoints
* [GET /v1/timestamp](#get-v1timestamp)
* [GET /v1/market/asset/id](#get-v1marketassetid)
* [GET /v1/market/asset/symbol](#get-v1marketassetsymbol)
* [GET /v1/market/fiat/id](#get-v1marketfiatid)
* [GET /v1/market/fiat/symbol](#get-v1marketfiatsymbol)
* [GET /v1/market/pair/list](#get-v1marketpairlist)
* [GET /v1/market/pair/symbol](#get-v1marketpairsymbol)
* [GET /v1/market/ticker/id](#get-v1markettickerid)
* [GET /v1/market/ticker/symbol](#get-v1markettickerid)
* [GET /v1/market/trade/list](#get-v1markettradelist)
* [GET /v1/market/bid/list](#get-v1marketbidlist)
* [GET /v1/market/ask/list](#get-v1marketasklist)
* [GET /v1/market/open/list](#get-v1marketopenlist)
* [GET /v1/market/tradingview](#get-v1markettradingview)

* [POST /v1/user/wallet/list/id](#post-v1userwalletlistid)
* [POST /v1/user/wallet/list/asset](#post-v1userwalletlistasset)
* [POST /v1/user/wallet/id](#post-v1userwalletid)


* [POST /v1/user/balance/list](#post-v1userbalancelist) -
* [POST /v1/user/balance/asset](#post-v1userbalanceasset) -
* [POST /v1/user/balance/fiat](#post-v1userbalancefiat) -

* [POST /v1/user/bid/place](#post-v1userbidplace) -
* [POST /v1/user/ask/place](#post-v1useraskplpace) -
* [POST /v1/user/order/list](#post-v1userorderlist) -
* [POST /v1/user/order/cancel](#post-v1userordercancel) -


# Constructing requests
## Request Header
Every request must contain following headers:
* Accept: application/json
* Content-Type: application/json
* X-WEX-APIKEY: {API KEY}
*Additionaly: "User's" requests requires authentication - signature have to be provided.*

## Payload
Payload format is always a JSON. Every payload must contain timestamp (`ts`)  in the query string (`?ts=CURRENT_TIMESTAMP` for both methods: `post` and `get`) and for user specified methods signature key (`sig`) is required.


### Example payload with out signature:
```javascript
{"asset":{"id":[51]},"ts":1567890123}
```
### Example payloadWith signature:
```javascript
{"asset":{"id":[51]},"ts":1567890123,"sig":"1e5ffc1dc3b5547950bb017133add50e}
```
Signature must equal to result of HMAC SHAcontatation of: `ts` and your {API SECRET}. If your {API KEY} equals: XYZ your signature should be like in the example above.


# API documentation
Refer to the following for description of each endpoint

### GET /v1/timestamp

#### Description:
Get the server timestamp. 
Your delta of your and our timestamp is not verified when you call this method.

#### Query (body):
* none

#### Response:
```javascript
{
  error: false,
  result: 1567890123
}
```


### GET /v1/market/asset/id

#### Description:
List all available assets (`id` is a key).

#### Query (body):
* none

#### Response:
```javascript
{
  "result": {
    "20": {
      "symbol": "GOLD",
      "name": "Gold",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "21": {
      "symbol": "SILV",
      "name": "Silver",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "22": {
      "symbol": "PLAT",
      "name": "Platinium",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "23": {
      "symbol": "COPP",
      "name": "Copper",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "51": {
      "symbol": "BTC",
      "name": "Bitcoin",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "52": {
      "symbol": "BCH",
      "name": "Bcash",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "53": {
      "symbol": "BTG",
      "name": "Bitcoin Gold",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "54": {
      "symbol": "ETH",
      "name": "Etherum",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 18,
        "current": 2
      }
    },
    "55": {
      "symbol": "LTC",
      "name": "Litecoin",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "56": {
      "symbol": "XLM",
      "name": "Stellar Lumens Coin",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 7,
        "current": 2
      }
    },
    "57": {
      "symbol": "XRP",
      "name": "Ripple",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "58": {
      "symbol": "ZEC",
      "name": "Zcash",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "59": {
      "symbol": "DASH",
      "name": "Dash",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "103": {
      "symbol": "USDT",
      "name": "Tether",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 0,
        "current": 2
      }
    }
  },
  "time": {
    "ts": 1570357380,
    "duration": 2.471097946166992
  },
  "error": null
}
```

### GET /v1/market/asset/symbol

#### Description:
List all available assets (`symbol` is a key).

#### Query (body):
* none

#### Response:
```javascript
{
  "result": {
    "BTC": {
      "id": 51,
      "name": "Bitcoin",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "BCH": {
      "id": 52,
      "name": "Bcash",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "BTG": {
      "id": 53,
      "name": "Bitcoin Gold",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "ETH": {
      "id": 54,
      "name": "Etherum",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 18,
        "current": 2
      }
    },
    "GOLD": {
      "id": 20,
      "name": "Gold",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "SILV": {
      "id": 21,
      "name": "Silver",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "PLAT": {
      "id": 22,
      "name": "Platinium",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "COPP": {
      "id": 23,
      "name": "Copper",
      "is_active": true,
      "is_market": false,
      "is_crypto": false,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "LTC": {
      "id": 55,
      "name": "Litecoin",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "XLM": {
      "id": 56,
      "name": "Stellar Lumens Coin",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 7,
        "current": 2
      }
    },
    "XRP": {
      "id": 57,
      "name": "Ripple",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "ZEC": {
      "id": 58,
      "name": "Zcash",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "DASH": {
      "id": 59,
      "name": "Dash",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "NMC": {
      "id": 100,
      "name": "Namecoin",
      "is_active": false,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "PPC": {
      "id": 101,
      "name": "Peercoin",
      "is_active": false,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 6,
        "current": 2
      }
    },
    "DOGE": {
      "id": 102,
      "name": "Dogecoin",
      "is_active": false,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 8,
        "current": 2
      }
    },
    "USDT": {
      "id": 103,
      "name": "Tether",
      "is_active": true,
      "is_market": false,
      "is_crypto": true,
      "precision": {
        "real": 0,
        "current": 2
      }
    }
  },
  "time": {
    "ts": 1570357415,
    "duration": 2.5266048908233643
  },
  "error": null
}
```


### GET /v1/market/fiat/id

#### Description:
List all available fiat currencies (`id` is a key).

#### Query (body):
* none

#### Response:
```javascript
{
  "result": {
    "11": {
      "symbol": "THB",
      "name": "Thai Bat",
      "is_active": true,
      "precision": {
        "real": 2,
        "current": 2
      }
    },
    "12": {
      "symbol": "EUR",
      "name": "Euro",
      "is_active": true,
      "precision": {
        "real": 2,
        "current": 2
      }
    },
    "13": {
      "symbol": "USD",
      "name": "US Dolar",
      "is_active": true,
      "precision": {
        "real": 2,
        "current": 2
      }
    }
  },
  "time": {
    "ts": 1570357356,
    "duration": 2.5558760166168213
  },
  "error": null
}
```

### GET /v1/market/fiat/symbol

#### Description:
List all available fiat currencies (`symbol` is a key).

#### Query:
* `ts` (int): Your timestamp

#### Response:
```javascript
{
  "result": {
    "THB": {
      "id": 11,
      "name": "Thai Bat",
      "is_active": true,
      "precision": {
        "real": 2,
        "current": 2
      }
    },
    "EUR": {
      "id": 12,
      "name": "Euro",
      "is_active": true,
      "precision": {
        "real": 2,
        "current": 2
      }
    },
    "USD": {
      "id": 13,
      "name": "US Dolar",
      "is_active": true,
      "precision": {
        "real": 2,
        "current": 2
      }
    }
  },
  "time": {
    "ts": 1570357293,
    "duration": 2.53281307220459
  },
  "error": null
}
```

### GET /v1/market/pair/list

#### Description:
List all available pairs.

#### Query (body):
* none

#### Response:
```javascript
{
  "result": [
    {
      "id": 1,
      "from": "11",
      "to": "51",
      "type": [
        "fiat",
        "asset"
      ],
      "pair": "THB_BTC",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 2,
      "from": "11",
      "to": "52",
      "type": [
        "fiat",
        "asset"
      ],
      "pair": "THB_BCH",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 3,
      "from": "11",
      "to": "53",
      "type": [
        "fiat",
        "asset"
      ],
      "pair": "THB_BTG",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 4,
      "from": "11",
      "to": "54",
      "type": [
        "fiat",
        "asset"
      ],
      "pair": "THB_ETH",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 5,
      "from": "11",
      "to": "55",
      "type": [
        "fiat",
        "asset"
      ],
      "pair": "THB_LTC",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 8,
      "from": "51",
      "to": "103",
      "type": [
        "asset",
        "asset"
      ],
      "pair": "BTC_USDT",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 10,
      "from": "54",
      "to": "103",
      "type": [
        "asset",
        "asset"
      ],
      "pair": "ETH_USDT",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 6,
      "from": "51",
      "to": "54",
      "type": [
        "asset",
        "asset"
      ],
      "pair": "BTC_ETH",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 7,
      "from": "51",
      "to": "57",
      "type": [
        "asset",
        "asset"
      ],
      "pair": "BTC_XRP",
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    {
      "id": 9,
      "from": "54",
      "to": "57",
      "type": [
        "asset",
        "asset"
      ],
      "pair": "ETH_XRP",
      "availability": {
        "ask": true,
        "bid": true
      }
    }
  ],
  "time": {
    "ts": 1570359912,
    "duration": 4.139039039611816
  },
  "error": null
}
```


### GET /v1/market/pair/symbol

#### Description:
List all available pairs (fiat|asset -> asset|fiat) (`{symbol_from}_{symbol_to}` is a key).

#### Query (body):
* none

#### Response:
```javascript
{
  "result": {
    "THB_BTC": {
      "id": 1,
      "from": "11",
      "to": "51",
      "type": [
        "fiat",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "THB_BCH": {
      "id": 2,
      "from": "11",
      "to": "52",
      "type": [
        "fiat",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "THB_BTG": {
      "id": 3,
      "from": "11",
      "to": "53",
      "type": [
        "fiat",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "THB_ETH": {
      "id": 4,
      "from": "11",
      "to": "54",
      "type": [
        "fiat",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "THB_LTC": {
      "id": 5,
      "from": "11",
      "to": "55",
      "type": [
        "fiat",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "BTC_USDT": {
      "id": 8,
      "from": "51",
      "to": "103",
      "type": [
        "asset",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "ETH_USDT": {
      "id": 10,
      "from": "54",
      "to": "103",
      "type": [
        "asset",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "BTC_ETH": {
      "id": 6,
      "from": "51",
      "to": "54",
      "type": [
        "asset",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "BTC_XRP": {
      "id": 7,
      "from": "51",
      "to": "57",
      "type": [
        "asset",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    },
    "ETH_XRP": {
      "id": 9,
      "from": "54",
      "to": "57",
      "type": [
        "asset",
        "asset"
      ],
      "availability": {
        "ask": true,
        "bid": true
      }
    }
  },
  "time": {
    "ts": 1570357084,
    "duration": 4.141546964645386
  },
  "error": null
}
```


### GET /v1/market/ticker/id

#### Description:
Get ticker information (`{pair_id}` is a key).

#### Query (body):
Optional query parameters (`from` | `to` | `pair`)
* `id` (array of integers) identifiers of pairs ```{"id":[1,2,8]}```,
* `from` (object) ```{"from":{"fiat": [11, 12], "asset":[51, 56]}}```,
* `to` (object) ```{"to":{"fiat": [11, 12], "asset":[51, 56]}}```,

//TODO

### GET /v1/market/ticker/symbol

#### Description:
Get ticker information (`{symbol_from}_{symbol_to}` is a key).

#### Query (body):
Optional query parameters (`from` | `to` | `pair`)
* `id` (array of integers) identifiers of pairs ```{"id":[1,2,8]}```,
* `from` (object) ```{"from":{"fiat": [11, 12], "asset":[51, 56]}}```,
* `to` (object) ```{"to":{"fiat": [11, 12], "asset":[51, 56]}}```,

//TODO

#### Response:
```javascript
{
  THB_BTC: {
    id: 1,
    current
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

### GET /v1/market/trade/list

### GET /v1/market/bid/list

### GET /v1/market/ask/list

### GET /v1/market/open/list



### POST /v1/user/wallet/list/id

#### Description:
List all available wallets / wallets filtered by asset ids. Identifier of the wallet is a key.

#### Query (body):
* `asset` (array of integers, optional): identifiers of assets ```{"asset":[51]}```

#### Response:
```javascript
{
  "result": {
    "5this_is_example_onlyaa97a3d72fe": {
      "address": "2this_is_example_onlyZNFs8CwDQwgFSF",
      "asset": 51,
      "is_blocked": false,
      "is_active": true
    }
  },
  "time": {
    "ts": 1570686849,
    "duration": 1.8354721069335938
  },
  "error": null
}
```

### POST /v1/user/wallet/list/asset

#### Description:
List all available wallets / wallets filtered by asset ids. Identifier of the asset is a key.
In case there will be more wallets for one asset ID then some of the keys could be an arrays instead of objects, that's why is better to call
* [POST /v1/user/wallet/list/id](#post-v1userwalletlistid) if you are not sure. Please note: aliases for wallet's are not causing asset keys to be an array.

#### Query (body):
* `asset` (array of integers, optional): identifiers of assets ```{"asset":[51,52]}```

#### Response:
```javascript
{
  "result": {
    "51": {
      "id": "5this_is_example_onlyaa97a3d72fe",
      "address": "2this_is_example_onlyZNFs8CwDQwgFSF",
      "is_blocked": false,
      "is_active": true
    },
    "52": [
    {
      "id": "5this_is_example_onlyaa97a3d7001",
      "address": "2this_is_example_onlyZNFs8CwDQw0001",
      "is_blocked": false,
      "is_active": true
    },
    {
      "id": "5this_is_example_onlyaa97a3d7002",
      "address": "2this_is_example_onlyZNFs8CwDQw0002",
      "is_blocked": false,
      "is_active": true
    }]
  },
  "time": {
    "ts": 1570687691,
    "duration": 1.8826661109924316
  },
  "error": null
}
```

### POST /v1/user/wallet/id

#### Description:
List all wallet's addresses. If you'll priovide identifiers and addresses then `IN(id) AND IN(address)` condition will be in use. If you will pass id or address of the alias you will get the NO_DATA error.

#### Query (body):
* `wallet` (object, required): identifiers or main addresses,
* `wallet->id` (array of strings): walet's identifiers ```{"wallet":{"id":["xyz"]}```,
* `wallet->address` (array of strings): wallet's identifiers ```{"wallet":{"address":["1xy"]}}```

#### Response:
```javascript
{
  "result": {
    "5this_is_example_onlyaa97a3d72fe": [
      {
        "address": "2NCthi_is_example_onlyNFs8CwDQwgFSF",
        "id": "5this_is_example_onlyaad1a7f0f77", //id of the address
        "chain": 0
      },
      {
        "address": "2Nthis_is_example_only85uUug3aR7zs4",
        "id": "5this_is_example_only4310e2a16dd", // id of the address
        "chain": 0
      }
    ]
  },
  "time": {
    "ts": 1570689969,
    "duration": 3.5230319499969482
  },
  "error": null
}
```


### POST /v1/user/balance/list
### POST /v1/user/balance/asset
### POST /v1/user/balance/fiat

### POST /v1/user/bid/place
### POST /v1/user/ask/place
### POST /v1/user/order/list
### POST /v1/user/order/cancel 


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
