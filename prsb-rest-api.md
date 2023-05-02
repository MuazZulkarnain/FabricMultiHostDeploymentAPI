# PRSB-Hyperledger-Fabric-Rest-API

This API allows you to trigger smart contract in the PRSB blockchain nodes

The API is available at `http://117.53.155.107:4000/channels/mychannel/chaincodes/prsb`

Authorization: Bearer Token
{{Token}} = eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOm51bGwsInVzZXJuYW1lIjoiQWRtaW4iLCJvcmdOYW1lIjoiT3JnMSIsImlhdCI6MTY4MjkwNjA5N30.zSWEGk2Ft_rDeNT-TInEKpLQYfaMkp27pEzsZ0hbJxc

## Endpoints

- [Generating Token](#Token)
- [Transfer Token](#Transfer)
- [Retire Token](#Retire)
- [Query Token](#Query)
- [Query Token History](#History)

## Token
### Create New Token

**`POST `**

**Parameters**

| Name            | Type    | In    | Required | Description                                      |
| --------------- | ------- | ----- | -------- | ------------------------------------------------ |
| `fcn`           | string  | body  | Yes      | Specifies the function you want to use           |
| `peers`         | string  | body  | Yes      | endorser peer involved in the transaction        |
| `chaincodeName` | string  | body  | Yes      | Name of the chaincode `prsb`                     |
| `channelName`   | string  | body  | Yes      | Name of the channel `mychannel`                  |
| `args`          | array   | body  | Yes      | Required to make the function works              |

**Status codes**

| Status code | Description                                            |
| ----------- | ------------------------------------------------------ |
| 20 OK       | Indicates that the  |

Example response body:

```
{
   "created": true,
   "cartId": "bx0-ycNjqIm5IvufuuZ09"
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
