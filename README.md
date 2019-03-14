CloudFront Invalidate Distribution

Make your AWS CodePipeline invoke this Lambda function to invalidate a CloudFront distribution.

### Prerequisites

Install the [Serverless Framework](https://serverless.com/) if you don't have it.

    npm install -g serverless

### Deploy

    git clone https://github.com/jweyrich/cloudfront-invalidate-dist.git
    cd cloudfront-invalidate-dist
    serverless deploy [--aws-profile yourProfile]

### Configure your CodePipeline

1. Open your CodePipeline
2. Create a new stage
3. Add a new action
4. In 'Action Provider' select 'AWS Lambda'
5. In 'Function name' select the deployed function
6. In 'User parameters' specify the desired CloudFront distribution and paths to be invalidated. Example:

    `{ "distributionId": "FP7AWS1WBJLKSX", "objectPaths": [ "/*" ] }`

7. Save the action
8. Test

### Examples of User Parameters

    { "distributionId": "FP7AWS1WBJLKSX", "objectPaths": [ "/*" ] }
    { "distributionId": "FP7AWS1WBJLKSX", "objectPaths": [ "/foo", "/bar/baz.jpg", "/bar/baz/*" ] }
