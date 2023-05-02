# PRSB-Hyperledger-Fabric-Rest-API

This API allows you to trigger smart contract in the PRSB blockchain nodes

The API is available at `http://117.53.155.107:4000/channels/mychannel/chaincodes/prsb`

## Endpoints

- [Generating Token](#Token)
- [Transfer Token](#Transfer)
- [Retire Token](#Retire)
- [Query Token](#Query)
- [Query Token History](#History)

## Bearer Token
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2OTg1NDcwMTQsInVzZXJuYW1lIjoiYWRtaW4xMCIsIm9yZ05hbWUiOiJPcmcxIiwiaWF0IjoxNjgyOTk1MDE0fQ.fBAhzmd5VZ2HmBcRRxzasKu-7rDLqLM_LbDWA1W3iAg

## Token
### Generating Token

**`POST `**

**Parameters**

| Name            | Type    | In    | Required | Description                                      |
| --------------- | ------- | ----- | -------- | ------------------------------------------------ |
| `fcn`           | string  | body  | Yes      | Specifies the function you want to use           |
| `args`          | array   | body  | Yes      | Required to make the function works              |

**Status codes**

| Status code      | Description                                            |
| -----------      | ------------------------------------------------------ |
| 201 OK           | Successfully generated the tokens                      |
| 400 Bad Request  | Function name is incorrect                             |
| 502 Bad Gateway  | Will need to retrigger the request                     |

Example response body:

```
{
    "result": {
        "message": "Successfully generated 10 tokens for TOKEN11!",
        "TxId": "8ebd94638299fbc21de209a0571624fd210c0c455b2355118fff0ff3e638cf85"
    },
    "error": null,
    "errorData": null
}
```


### Get a product

**`GET /products/:productId`**

Returns a single product from the inventory.

**Parameters**

| Name            | Type    | In    | Required | Description                                      |
| --------------- | ------- | ----- | -------- | ------------------------------------------------ |
| `productId`     | integer | path  | Yes      | Specifies the product's id you wish to retrieve. |
| `product-label` | boolean | query | No       | Returns the product label in PDF format.         |

**Status codes**

| Status code   | Description                                               |
| ------------- | --------------------------------------------------------- |
| 200 OK        | Indicates a successful response.                          |
| 404 Not found | Indicates that there is no product with the specified id. |
