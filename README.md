# Lambda Notes
1. AWS Lambda is a compute service that lets you run code without provisioning or managing servers.
2. Lambda is an ideal compute service for application scenarios that need to scale up rapidly, and scale down to zero when not in demand.
3. Because Lambda manages memory, CPU, network and other resources, you cannot log in to compute instances or customize the operating system on provided runtimes.
4. With serverless computing, your application still runs on servers, but all the server management is done by AWS.
5. AWS Lambda natively supports Java, Go, PowerShell, Node.js, C#, Python, and Ruby code, and provides a Runtime API which allows you to use any additional programming languages.
6. We cannot access the infrastructure that AWS Lambda runs on.
7. Each AWS Lambda function runs in its own isolated environment, with its own resources and file system view.
8. A function is a resource that you can invoke to run your code in Lambda. Lambda runs instances of your function to process events. A trigger is a resource or configuration that invokes a Lambda function. An event is a JSON-formatted document that contains data for a Lambda function to process.
9. An execution environment provides a secure and isolated runtime environment and manages the processes, resources required to run the function.
10. Lambda supports two types of deployment packages: A .zip file archive that contains your function code and its dependencies. A container image that is compatible with the Open Container Initiative (OCI) specification.
11. Lambda supports multiple languages through the use of runtimes. A runtime provides a language-specific environment that relays invocation events, context information, and responses between Lambda and the function.
12. A Lambda alias is a pointer to a function version that you can update.
13.  Lambda creates a new version of your function each time that you publish the function.
14. AWS Lambda stores code in Amazon S3 and encrypts it at rest. AWS Lambda performs additional integrity checks while your code is in use.
15. A function is an object that is able to accept some sort of input, possibly modify it, and return some sort of output.
16. You can configure each Lambda function with its own ephemeral storage between 512MB and 10,240MB, in 1MB increments. The ephemeral storage is available in each function’s /tmp directory.
17. All data stored in ephemeral storage is encrypted at rest with a key managed by AWS.
18. If durable, persistent storage, is required by your application consider using Amazon S3 or Amazon EFS. If storing data needed by code in a single function invocation, consider using AWS Lambda ephemeral storage.
19. Inbound network connections are blocked by AWS Lambda. TCP port 25 traffic is also blocked as an anti-spam measure.
20. Package any code (frameworks, SDKs, libraries, and more) as a Lambda Layer and manage and share them easily across multiple functions.
21. AWS Lambda automatically integrates with Amazon CloudWatch logs, creating a log group for each Lambda function and providing basic application lifecycle event log entries, including logging the resources consumed for each use of that function.
22. Every time an event notification is received for your function, AWS Lambda quickly locates free capacity within its compute fleet and runs your code.
23. In the AWS Lambda resource model, you choose the amount of memory you want for your function, and are allocated proportional CPU power and other resources.
24. You can set your memory from 128MB to 10,240MB.
25. AWS Lambda functions can be configured to run up to 15 minutes per execution. You can set the timeout to any value between 1 second and 15 minutes.
26. An event source is an AWS service or developer-created application that produces events that trigger an AWS Lambda function to run. Some services publish these events to Lambda by invoking the cloud function directly (for example, Amazon S3). Lambda can also poll resources in other services that do not publish events to Lambda.
27. Events are passed to a Lambda function as an event input parameter.
28. AWS Lambda enables you to package and deploy functions as container images.
29. Use Docker CLI to build the image, upload it to Amazon ECR, and then create the function by using all familiar Lambda interfaces and tools, such as the AWS Management Console, the AWS CLI, the AWS SDK, AWS SAM, and AWS CloudFormation.
30. Lambda supports images with a size of up to 10GB. Functions created using ZIP archives have a maximum code package size of 250 MB unzipped.
31. All existing AWS Lambda features, with the exception of Lambda layers and Code Signing, can be used with functions deployed as container images.
32. Lambda uses Amazon ECR as the underlying code storage for functions defined as container images.
33. ZIP functions are automatically patched for the latest runtime security and bug fixes.
34. AWS Lambda SnapStart for Java delivers up to 10x faster function startup performance.
35. With Lambda SnapStart, Lambda initializes the one-time initialization function code ahead of time when you publish a function version, instead of when you first invoke the function. Then, Lambda takes a snapshot and caches the memory and disk state of the initialized  execution environment.
36. Lambda SnapStart and Provisioned Capacity cannot be enabled at the same time, on the same function.
37. There's no additional cost for enabling Lambda SnapStart.
38. When enabled, Provisioned Concurrency keeps functions initialized and hyper-ready to respond in double-digit milliseconds.
39. If the concurrency of a function reaches the configured level, subsequent invocations of the function have the latency and scale characteristics of regular Lambda functions.
40. With Amazon Elastic File System (Amazon EFS) for AWS Lambda, customers can securely read, write and persist large volumes of data.
41. Connect an existing EFS file system to a Lambda function via an EFS Access Point.
42. To use EFS, AWS Lambda function needs to be configured to access that VPC.
43. Data is encrypted when in transit and at rest between AWS Lambda functions and the Amazon EFS file systems.
44. To use Lambda@Edge, upload your Node.js or Python code to AWS Lambda and configure your function to be triggered in response to Amazon CloudFront requests. The code is then ready to execute across AWS locations globally when a request for content is received.
45. There are no maintenance windows or scheduled downtimes for either Lambda service or Lambda function.
46. On exceeding the maximum concurrent executions limit, AWS Lambda functions being invoked synchronously will return a throttling error (429 error code).
47. Lambda functions being invoked asynchronously can absorb reasonable bursts of traffic for approximately 15-30 minutes, after which incoming events will be rejected as throttled.
48. Each synchronously invoked Lambda function can scale at a rate of up to 1000 concurrent executions every 10 seconds.
49. On failure, Lambda functions being invoked synchronously will respond with an exception. Lambda functions being invoked asynchronously are retried at least 3 times.
50. On exceeding the retry policy for asynchronous invocations, you can configure a “dead letter queue” (DLQ) into which the event will be placed.
51. You can configure an Amazon SQS queue or an Amazon SNS topic as your dead letter queue.
52. Code Signing for AWS Lambda offers trust and integrity controls that enable you to verify that only unaltered code from approved developers is deployed in your Lambda functions.
53. You can use Amazon Step Functions to coordinate multiple invoking Lambda functions. You can invoke multiple Lambda functions serially, passing the output of one to the other, or in parallel.
54. Lambda counts a request each time it starts executing in response to an event notification trigger, such as from Amazon Simple Notification Service (SNS) or Amazon EventBridge, or an invoke call, such as from Amazon API Gateway, or via the AWS SDK, including test invokes from the AWS Console.
55. You are charged based on the number of requests for your functions and the duration it takes for your code to execute.
56. You can run your Lambda functions on processors built on either x86 or Arm architectures. Arm delivers up to 34% better price performance compared to functions running on x86 processors.
