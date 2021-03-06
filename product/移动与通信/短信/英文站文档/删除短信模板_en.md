## API Description
### Description
This API is used to delete SMS text message (or voice message) templates.

### URL Example
`POST https://yun.tim.qq.com/v5/tlssmssvr/del_template?sdkappid=xxxxx&random=xxxx`
**Note**: Replace `xxxxx` in the field `sdkappid=xxxxx` with the sdkappid you applied for on Tencent Cloud, and replace `xxxx` in the field `random=xxxx` with a random number.

## Request Parameters
```json
{
    "sig": "c13e54f047ed75e821e698730c72d030dc30e5b510b3f8a0fb6fb7605283d7df",
    "time": 1457336869,
    "tpl_id": [
        123,
        124
    ]
}
```

| Parameter | Required | Type | Description |
|--------|------|--------|--------------------------------------------------------------------|
| sig | Yes | String | App credential. For more information on how to calculate, please see below. |
| time | Yes | Number | The time when the request is initiated. It is expressed as a Unix timestamp. A failure message is returned if the time difference between the Unix timestamp and the system time is greater than 10 minutes. |
| tpl_id | Yes | Array | An array of IDs of templates to be deleted |
**Note**:
The "sig" field is generated based on the formula sha256(appkey=$appkey&random=$random&time=$time)
The pseudo code is as follows:
```
string strAppkey = "5f03a35d00ee52a21327ab048186a2c4"; //The appkey for the sdkappid, which must be kept confidential
string strRand = "7226249334"; //The value of the "random" field in the URL
string strTime = "1457336869"; //The Unix timestamp
string sig = sha256(appkey=5f03a35d00ee52a21327ab048186a2c4&random=7226249334&time=1457336869)
           = c13e54f047ed75e821e698730c72d030dc30e5b510b3f8a0fb6fb7605283d7df;
```

## Response Parameters
```json
{
    "result": 0,
    "msg": ""
}
```

| Parameter | Required | Type | Description |
|--------|------|--------|------------------------------------------|
| result | Yes | Number | Error code. 0: Successful (basis for billing). Other values: Failed |
| msg | Yes | String | Error message. The error message returned when the "result" is not 0 |
