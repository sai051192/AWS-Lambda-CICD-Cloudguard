**

## CICD Pipeline using code pipeline and GitHub Actions for Lambda apps, secured by CloudGuard Serverless Security

**

This GitHub Repo contains the supporting code and adjoined brief for the video demonstration of 'CICD pipeline for Lambda app - secured by Check Point CloudGuard Serverless' (https://www.youtube.com/watch?v=ViF9dssMTFw). GitHub Actions, AWS CodeBuild, Code Pipeline and CloudFormation are used in the pipeline. CloudGuard Severless Security provides code scanning and runtime application security.

![](https://github.com/sai051192/AWS-Lambda-CICD-Cloudguard/blob/main/cicdDiagram.jpg?raw=true)

**CloudGuard Serverless Security**

CloudGuard Serverless security automates security & visibility for cloud native serverless applications from development to runtime, enabling organizations to securely innovate at cloud speed. By analyzing the serverless application code before and after deployment, organizations can achieve a continuous serverless security posture–automating application hardening, minimizing the attack surface, and simplifying governance. Utilizing machine-based analysis and deep learning algorithms, CloudGuard builds a model of normal application and function behavior to detect and block application-layer attacks for enhanced serverless security. 
Refer to https://www.checkpoint.com/products/cloudguard-serverless-security/ for more details.

![](https://github.com/sai051192/AWS-Lambda-CICD-Cloudguard/blob/main/CloudGuardServerlessInfoGraph.png?raw=true)

**CloudGuard Serverless Code Scan ( Proact)**

CloudGuard Dome9 Code scan assess the risk in serverless functions in your AWS cloud accounts. CloudGuard code scan performs SAST, SCA and accesses the function role for unnecessary IAM permissions. It then calculates a Posture score, based on the number, nature, and severity of vulnerabilities found, and generates alerts for each vulnerability, that indicate the specific issues and, in many cases, the actions necessary to remedy them. The CloudGuard Code Scan is performed during the push and pull requests in GitHub using GitHub Actions.

   

    cloudguard proact -m template.yaml -t CLOUDGUARD_API_ID:secrets.CLOUDGUARD_API_SECRET

**CloudGuard Serverless Function Runtime Protection (FSP)**

You can apply CloudGuard Runtime protection to serverless functions at runtime. This protects functions from malicious inputs or attacks, by monitoring the function behavior for anomalous behavior, and by acting as a workload firewall for inputs from malicious sources. It does this without modifying the source code of the function, and with minimal impact on the runtime performance of the function. When you apply protection, CloudGuard adds a small module via Lambda layers to your function that is loaded in runtime, along with the function. This module is small and, since it is separate from your function code, does not affect the behavior of the function. It monitors your function, while adding very little runtime overhead. It is also fully transparent - all reporting is done using the function logs, so you can review the metadata it collects. Runtime protection dynamically inspects various points within the flow of functions, using mechanisms such as pattern matching, flow analysis, blacklisting, whitelisting, and applies policies such as reporting and blocking in response to suspicious activity.

    cloudguard fsp add -t CLOUDGUARD_API_ID:CLOUDGUARD_API_KEY -C template.yaml --region us-east-1 --output outputtemplate.yaml

**GitHub Actions**

GitHub Actions help you automate tasks within your software development life cycle. GitHub Actions are event-driven, meaning that you can run a series of commands after a specified event has occurred. For example, every time someone creates a pull request for a repository, you can automatically run a command that executes a software testing script.

GitHub actions are used here to perform Code scanning at the time of ‘push’ and ‘pull request’. Refer to https://github.com/sai051192/AWS-Lambda-CICD-Cloudguard/blob/main/code-scan.yml for the workflow code.

**AWS CodePipeline**

AWS CodePipeline is a fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates. CodePipeline automates the build, test, and deploy phases of your release process every time there is a code change, based on the release model you define. This enables you to rapidly and reliably deliver features and updates. You can easily integrate AWS CodePipeline with third-party services such as GitHub or with your own custom plugin.

![product-page-diagram_CodePipeLine](https://github.com/sai051192/AWS-Lambda-CICD-Cloudguard/blob/main/Codepipeline.png?raw=true)

**AWS CodeBuild**

AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy. With CodeBuild, you don’t need to provision, manage, and scale your own build servers. CodeBuild scales continuously and processes multiple builds concurrently, so your builds are not left waiting in a queue. You can get started quickly by using prepackaged build environments, or you can create custom build environments that use your own build tools.

Code Build is used to convert the SAM template into cloudformation template and integrate Cloudguard Runtime Protection into the Cloudformation template

**AWS CloudFormation**

AWS CloudFormation gives you an easy way to model a collection of related AWS and third-party resources, provision them quickly and consistently, and manage them throughout their lifecycles, by treating infrastructure as code. A CloudFormation template describes your desired resources and their dependencies so you can launch and configure them together as a stack. You can use a template to create, update, and delete an entire stack as a single unit, as often as you need to, instead of managing resources individually. AWS SAM templates are an extension of AWS CloudFormation templates, with some additional components that make them easier to work with. You use the AWS SAM specification to define your serverless application and other related attributes such as resources types, resource properties, data types, resource attributes, intrinsic functions, and API Gateway extensions.

**AWS Lambda**

AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers, creating workload-aware cluster scaling logic, maintaining event integrations, or managing runtimes. With Lambda, you can run code for virtually any type of application or backend service - all with zero administration. Just upload your code as a ZIP file or container image, and Lambda automatically and precisely allocates compute execution power and runs your code based on the incoming request or event, for any scale of traffic

**AWS API Gateway**

Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the "front door" for applications to access data, business logic, or functionality from your backend services. Using API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. API Gateway supports containerized and serverless workloads, as well as web applications.
