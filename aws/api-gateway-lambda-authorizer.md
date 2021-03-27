# AWS API Gateway Custom Lambda Authorizer
- Use an authorizer function to secure private api endpoints
- The authorizer function must return a correctly-shaped policy document object, otherwise API Gateway will fail to give permission

## Sample authorizer function
```js
module.exports.handler = async (event, context) => {

  // Do token verification here

  const policyDocument = {
    Version: "2012-10-17",
    Statement: [
      {
        Action: "execute-api:Invoke",
        Effect: "Allow",
        Resource: "arn:aws:execute-api:{regionId}:{accountId}:{apiId}/{stage}/{httpVerb}/[{resource}/[{child-resources}]]"
      }
    ]
  }

  return {
    principalId,
    policyDocument,
    context: {
      "stringKey": "value",
      "numberKey": "1",
      "booleanKey": "true"
      // Notice that you cannot set a JSON object or array as a valid value of any key in the context map
    }
  }
}
```

## Experiences
- I had an issue where the authorizer function fails (it returns a 500 with AuthorizerConfigurationException) just because I misspelt "Version: **2012**-10-17" with "Version: **2021**-10-17" LMAO
- Also, these kinds of exception are not being logged to CloudWatch. I had to manually enable it to see the exception logs
-
## Enable API Gateway CloudWatch logs
1. Go to API Gateway > API
2. Stages > Logs/Tracing
3. Check `Enable CloudWatch Logs`,select `ERROR` for `Log level` and check `Log full requests/responses data`
4. You should see now the logs in CloudWatch in log group `API-Gateway-Execution-Logs_{api-identifier}`

## Resources
- https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-lambda-authorizer-output.html
- https://gist.github.com/djm/15cf09b6b21c20332a602d3bca6b6d08
