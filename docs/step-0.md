# Step 0 - Deploy the Cloudformation Stacks

To run the lab, you will need to deploy the [WAF Security Automations Solution](https://aws.amazon.com/solutions/aws-waf-security-automations/) and a sample Web App that we'll use for testing.

> **Note**  
You are responsible for the cost of the AWS services used while running these CloudFormation stacks. There is no additional cost for using them. For full details, see the pricing pages for each AWS service you will be using in these CloudFormation stacks. Prices are subject to change.

## Deploy the WAF Security Automations Solution

|Region|Launch Template|
|------|---------------|
|**US East (N. Virginia)** (us-east-1) | [![Deploy AWS WAF Security Automations Solution](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=AWSWAFSecurityAutomations&templateURL=https://s3.amazonaws.com/solutions-reference/aws-waf-security-automations/v2.3.0/aws-waf-security-automations.template)|
|**US East (Ohio)** (us-east-2) | [![Deploy AWS WAF Security Automations Solution](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=AWSWAFSecurityAutomations&templateURL=https://s3.amazonaws.com/solutions-reference/aws-waf-security-automations/v2.3.0/aws-waf-security-automations.template)|
|**US West (Oregon)** (us-west-2) | [![Deploy AWS WAF Security Automations Solution](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=AWSWAFSecurityAutomations&templateURL=https://s3.amazonaws.com/solutions-reference/aws-waf-security-automations/v2.3.0/aws-waf-security-automations.template)|
|**EU (Ireland)** (eu-west-1) | [![Deploy AWS WAF Security Automations Solution](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=AWSWAFSecurityAutomations&templateURL=https://s3.amazonaws.com/solutions-reference/aws-waf-security-automations/v2.3.0/aws-waf-security-automations.template)|
|**EU (London)** (eu-west-2) | [![Deploy AWS WAF Security Automations Solution](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-2#/stacks/new?stackName=AWSWAFSecurityAutomations&templateURL=https://s3.amazonaws.com/solutions-reference/aws-waf-security-automations/v2.3.0/aws-waf-security-automations.template)|

Step by step instructions:
* Provide your stack with a unique name. *Note: Be careful not to exceed the 64-character stack name limit*
* Provide the following template parameters:
  * **Activate HTTP Flood Protection** = "yes - AWS Lambda log parser"
  * **Activate Scanner & Probe Protection** = "yes - Amazon Athena log parser"
  * **Endpoint Type** = "ALB"
  * **Application Access Log Bucket Name** (must be all lower case to match regex) = `<enter a random bucket name here>`
  * Leave all other parameters set to their default values.
* Continue through the remaining pages using the default values.
* On the final page, check the box at the bottom allowing AWS CloudFormation to create IAM resources with custom names.
* Click the orange "Create stack" button at the bottom-right of the page to deploy the stack into your account.
 
## Deploy the sample Web App

|Region|Launch Template|
|------|---------------|
|**US East (N. Virginia)** (us-east-1) | [![Deploy WAF Workshop Sample Web App](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=WAFWorkshopSampleWebApp&templateURL=https://solution-builders-us-east-1.s3.us-east-1.amazonaws.com/aws-waf-workshop/latest/main.template)|
|**US East (Ohio)** (us-east-2) | [![Deploy WAF Workshop Sample Web App](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=WAFWorkshopSampleWebApp&templateURL=https://solution-builders-us-east-2.s3.us-east-2.amazonaws.com/aws-waf-workshop/latest/main.template)|
|**US West (Oregon)** (us-west-2) | [![Deploy WAF Workshop Sample Web App](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=WAFWorkshopSampleWebApp&templateURL=https://solution-builders-us-west-2.s3.us-west-2.amazonaws.com/aws-waf-workshop/latest/main.template)|
|**EU (Ireland)** (eu-west-1) | [![Deploy WAF Workshop Sample Web App](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=WAFWorkshopSampleWebApp&templateURL=https://solution-builders-eu-west-1.s3.eu-west-1.amazonaws.com/aws-waf-workshop/latest/main.template)|
|**EU (London)** (eu-west-2) | [![Deploy WAF Workshop Sample Web App](deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-2#/stacks/new?stackName=WAFWorkshopSampleWebApp&templateURL=https://solution-builders-eu-west-2.s3.eu-west-2.amazonaws.com/aws-waf-workshop/latest/main.template)|

Step by step instructions:
* Provide your stack with a unique name. *Note: Be careful not to exceed the 64-character stack name limit*
* Continue through the remaining pages using the default values.
* On the final page, check the box at the bottom allowing AWS CloudFormation to create IAM resources with custom names.
* Click the orange "Create stack" button at the bottom-right of the page to deploy the stack into your account.

# [Next step](step-1.md)