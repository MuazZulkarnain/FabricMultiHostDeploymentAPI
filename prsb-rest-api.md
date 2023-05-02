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

Example request body:

```
{
    "fcn": "generateToken",
   "args": ["TOKEN11",10,"PRSB-C","PRSB-D",0.999]
}
```

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


### Query Token

**`GET `**

Returns the current token values

**Parameters**

| Name            | Type    | In    | Required | Description                                      |
| --------------- | ------- | ----- | -------- | ------------------------------------------------ |
| fcn             | string  | query | Yes      | Must be exactly 'queryToken'                     |
| args            | array   | query | Yes      | The specific token that wants to be queried      |

**Status codes**

| Status code      | Description                                            |
| -----------      | ------------------------------------------------------ |
| 200 OK           | Successfully generated the tokens                      |
| 400 Bad Request  | Either function name or token id is incorrect          |
| 502 Bad Gateway  | Will need to retrigger the request                     |

Example request parameters:

```
| Key              | Values                                                 |
| -----------      | ------------------------------------------------------ |
| fcn              | queryToken                                             |
| args             | ["TOKEN1"]                                             |
```

Example response body:

```
{
    "result": {
        "amount": 45,
        "owner": "PRSB-C",
        "source": "PRSB-D",
        "conversion_rate": 0.999,
        "past_operation": "Token Retired"
    },
    "error": null,
    "errorData": null
}
```
