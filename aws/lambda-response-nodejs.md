# Lambda response format
- API Gateway expects a correct response format

```js
exports.handler = (event, context, callback) => {

    var responseBody = {
        "key3": "value3",
        "key2": "value2",
        "key1": "value1"
    };

    var response = {
        "statusCode": 200,
        "headers": {
            "my_header": "my_value"
        },
        "body": JSON.stringify(responseBody),
        "isBase64Encoded": false
    };
    callback(null, response);
};
```

## Experiences
- I forget about this everytime. I'd spend minutes to debug my code in VSCode and in Cloudwatch only to learn that I have a malformed response

## Resources
- https://aws.amazon.com/premiumsupport/knowledge-center/malformed-502-api-gateway/
