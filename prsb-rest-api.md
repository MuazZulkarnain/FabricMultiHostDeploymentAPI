# PRSB-Hyperledger-Fabric-Rest-API

This API allows you to trigger smart contract in the PRSB blockchain nodes

The API is available at `http://117.53.155.107:4000/channels/mychannel/chaincodes/prsb`

Authorization: Bearer Token
{{Token}} = eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2ODE3NDY1OTksInVzZXJuYW1lIjoiVXNlcjM1Iiwib3JnTmFtZSI6Ik9yZzEiLCJpYXQiOjE2ODE3MTA1OTl9.goJ4rrJmjPF7n-9FJt-0DbmTgJlt4gpZItk6tzEvk2I

## Endpoints

- [Generating Token](#Token)
  - [Create New Token](#Create)
  - [Generate New/Old Token](#Generate)
- [Modifying Token Properties](#Properties)
  - [Change Token Owner](#Owner)
  - [Update Token Volume](#Volume)
- [Transfer Token](#Transfer)
- [Retire Token](#Retire)
  - [Retire All Token](#Retire-all)
  - [Retire Partial Token](#Retire-partial)

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