# PRSB-Hyperledger-Fabric-Rest-API

This API allows you to trigger smart contract in the PRSB blockchain nodes

The API is available at `http://117.53.155.107:4000/channels/mychannel/chaincodes/prsb`

## Endpoints

- [Generating Token](#Generating-Token)
- [Transfer Token](#Transfer-Token)
- [Retire Token](#Retire-Token)
- [Query Token](#Query-Token)
- [Query Token History](#Query-Token-History)

## Bearer Token
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2OTg1NDcwMTQsInVzZXJuYW1lIjoiYWRtaW4xMCIsIm9yZ05hbWUiOiJPcmcxIiwiaWF0IjoxNjgyOTk1MDE0fQ.fBAhzmd5VZ2HmBcRRxzasKu-7rDLqLM_LbDWA1W3iAg

## Generating Token
**`POST `**

**Parameters**

| Name            | Type    | In    | Required | Description                                                     |
| --------------- | ------- | ----- | -------- | --------------------------------------------------------------- |
| `fcn`           | string  | body  | Yes      | "generateToken"                                                 |
| `args`          | array   | body  | Yes      | ["ProjectID", tokenAmount, "Owner", "Source", conversionRate]   |

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


## Transfer Token
**`POST `**

**Parameters**

| Name            | Type    | In    | Required | Description                                                 |
| --------------- | ------- | ----- | -------- | ----------------------------------------------------------- |
| `fcn`           | string  | body  | Yes      | "transferToken"                                             |
| `args`          | array   | body  | Yes      | ["RequestedProjectID", "TransferredProjectID", tokenAmount] |

**Status codes**

| Status code      | Description                                            |
| -----------      | ------------------------------------------------------ |
| 201 OK           | Successfully transferred the tokens                    |
| 400 Bad Request  | Function name is incorrect or ProjectID doesnt exist   |
| 502 Bad Gateway  | Will need to retrigger the request                     |

Example request body:

```
{
    "fcn": "transferToken",
   "args": ["TOKEN9","TOKEN11",20.1]
}
```

Example response body:

```
{
    "result": {
        "message": "Successfully transferred 20.1 tokens to TOKEN11!",
        "TxId": "8ebd94638299fbc21de209a0571624fd210c0c455b2355118fff0ff3e638cf85"
    },
    "error": null,
    "errorData": null
}
```


## Retire Token
**`POST `**

**Parameters**

| Name            | Type    | In    | Required | Description                  |
| --------------- | ------- | ----- | -------- | ---------------------------- |
| `fcn`           | string  | body  | Yes      | "retirePartialToken"         |
| `args`          | array   | body  | Yes      | ["ProjectID", tokenAmount]   |

**Status codes**

| Status code      | Description                                          |
| -----------      | ---------------------------------------------------- |
| 201 OK           | Successfully retired the tokens                      |
| 400 Bad Request  | Function name is incorrect or ProjectID doesnt exist |
| 502 Bad Gateway  | Will need to retrigger the request                   |

Example request body:

```
{
    "fcn": "retirePartialToken",
   "args": ["TOKEN11", 2.5]
}
```

Example response body:

```
{
    "result": {
        "message": "Successfully retired 2.5 tokens!",
        "TxId": "8ebd94638299fbc21de209a0571624fd210c0c455b2355118fff0ff3e638cf85"
    },
    "error": null,
    "errorData": null
}
```

## Query Token

**`GET `**

Returns the current token values

**Parameters**

| Name            | Type    | In    | Required | Description   |
| --------------- | ------- | ----- | -------- | ------------- |
| fcn             | string  | query | Yes      | 'queryToken'  |
| args            | array   | query | Yes      | ["ProjectID"] |

**Status codes**

| Status code      | Description                                    |
| -----------      | ---------------------------------------------- |
| 200 OK           | Successfully queried the token                 |
| 400 Bad Request  | Either function name or ProjectID is incorrect |
| 502 Bad Gateway  | Will need to retrigger the request             |
 
Example request parameters:

```
| Key    | Values     |
| ------ | ---------- |
| fcn    | queryToken |
| args   | ["TOKEN1"] |
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


## Query Token History

**`GET `**

Returns the current token values

**Parameters**

| Name            | Type    | In    | Required | Description         |
| --------------- | ------- | ----- | -------- | ------------------- |
| fcn             | string  | query | Yes      | 'queryTokenHistory' |
| args            | array   | query | Yes      | ["ProjectID"]       |

**Status codes**

| Status code      | Description                                    |
| -----------      | ---------------------------------------------- |
| 200 OK           | Successfully queried the token history         |
| 400 Bad Request  | Either function name or ProjectID is incorrect |
| 502 Bad Gateway  | Will need to retrigger the request             |

Example request parameters:

```
| Key              | Values            |
| -----------      | ----------------- |
| fcn              | queryTokenHistory |
| args             | ["TOKEN1"]        |
```

Example response body:

```
{
    "result": [
        {
            "TxId": "becd001f8ab3762d440dce001fd8c77353d54e8ca88fa5c0c302d18e926c5b77",
            "Value": {
                "amount": 30,
                "owner": "PRSB-C",
                "source": "PRSB-D",
                "conversion_rate": 0.999,
                "past_operation": "Token Generated"
            },
            "Timestamp": "2023-05-02 04:00:12.978 +0000 UTC",
            "IsDelete": "false"
        },
        {
            "TxId": "00580e7fa7a9269ca80311bc9326eb0e5d624d0ad810e157dda0523034c4b26e",
            "Value": {
                "amount": 10,
                "owner": "PRSB-C",
                "source": "PRSB-D",
                "conversion_rate": 0.999,
                "past_operation": "Token Generated"
            },
            "Timestamp": "2023-05-02 04:00:03.409 +0000 UTC",
            "IsDelete": "false"
        }
    ],
    "error": null,
    "errorData": null
}
```
