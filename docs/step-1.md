# Step 1 - Getting Started with AWS WAF Security Automations Solution

## 1.1 Associate the solution's AWS WAF Web ACL with your ALB

After deploying the Web App, look at the [CloudFormation Exports](https://console.aws.amazon.com/cloudformation/home?#/exports). You should have a value called `site-url`. That is the address of the Application Load Balancer sitting on top of the Web App. Take note of that URL.

Next, you need to associate the solution's AWS WAF Web ACL with your ALB. For that:
* Go to the [AWS WAF console](https://console.aws.amazon.com/wafv2/home?#/webacls)
* Check if the region drop-down filter (not the one on the top, the one in the page) is selected with your region as value. For instance, "EU (Ireland)"
* Select the solution's WebACL - for instance "AWSWAFSecurityAutomations"
* On the right panel, select the "Rules" tab
* Scroll down to "AWS resources using this web ACL" section and click the "Add association" button
* On the "Resource type" drop-down, select "Application load balancer"
* On the "Resource" drop-down, select the ALB you've created
* Finally, click the "Add" button.


## 1.2 SQL Injection and XSS

Access the `site-url` endpoint and include bad signatures to the requests. You can use, for example:

* SQL Injection: `<your-endpoint>/?username=1'%20or%20'1'%20=%20'1&password=1'%20or%20'1'%20=%20'1'`
* XSS: `<your-endpoint>/?<SCRIPT>alert(“Cookie”+document.cookie)</SCRIPT>`

## 1.3 HTTP Flood (AWS Lambda log parser)

To test HTTP Flood, you can simulate an WAF log file deliver event. For that:

* Go to the CloudFormation stack's `Outputs` tab and search for the value defined for `WafLogBucket`
* Go to S3, and upload [this file](files/waf-access-log-sample.gz) to the `WafLogBucket` bucket
* Wait a few seconds (while the log parser function processes the new WAF log file)
* Check if the file `<stack_name>-waf_log_out.json` was added to the `WafLogBucket` bucket
* Go to [AWS WAF console](https://console.aws.amazon.com/wafv2/home?#/webacls) and check if `HTTP Flood` rule contains any IP listed

## 1.4 Scanners & Probe (Amazon Athena log parser)

To test Scanners & Probe, you can simulate a CloudWatch event running a query in a bucket that contains a sample access log file.
For that:
* Go to the S3 bucket that you set as Access Log Bucket. If you don't remember, go to stack's `Outputs` tab and search for the value defined for `AppAccessLogBucket`
* Create a new folder and name it AWSLogs and upload [this file](files/alb-access-log-sample.gz) to it

This file will be processed during the next scheduled *Scanner and Probe* scan. Rather than wait, we will run it on demand.

* Go to the [AWS Lambda console](https://console.aws.amazon.com/lambda/home)
* Open the `<stack_name>-LambdaLogParserFunction-<ID>` lambda function
* Follow the link related the CloudWatch scheduled event
* Copy the event data and create a Lambda test event with that information
* Run the lambda function using the same event data used by the scheduled event
* Wait a few seconds (while Athena processes the data, save the result back on S3 and the log parser function is called again to process the result file)
* Go to [AWS WAF console](https://console.aws.amazon.com/wafv2/home?#/webacls) and check if `Scanners & Probes` rule contains any IP listed

# [Next step](step-2.md)
