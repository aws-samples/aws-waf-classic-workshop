# AWS WAF workshop

> :warning: **This workshop uses AWS WAF Classic**

A workshop about [AWS WAF](https://aws.amazon.com/waf/) and the [WAF Security Automations Solution](https://aws.amazon.com/solutions/aws-waf-security-automations/)


## Introduction

This workshop introduces AWS WAF and the AWS WAF Security Automations solution.

The AWS WAF enables customers to create rules to block common attack patterns, administered via APIs.
The Security Automation Solution extends WAF by deploying a set of preconfigured rules to protect applications. These rules can be customised for your application.

## Learning Objectives

* Understand the built in functionality provided by AWS WAF
* Understand how the Security Automation Solution extends AWS WAF
* Understand how to configure the Security Automation Solution

## Prerequisites

To complete this workshop you will require the following:
* An AWS Account.
    * If you don’t already have an AWS account, create one at <https://aws.amazon.com> by following the on-screen instructions
* Your access to the AWS account must have IAM permissions to launch AWS CloudFormation templates that create IAM roles.

## Contents

### [Step 0 - Deploy the Cloudformation Stacks](docs/step-0.md)

In step 0 you will deploy the AWS resources required for later steps of the workshop.

### [Step 1 - Getting Started with AWS WAF Security Automations Solution](docs/step-1.md)

In step 1 you will set up the AWS WAF with an example web application and explore how the AWS WAF Security Automation Solution blocks three common types of attack.
* SQL Injection & Cross Site Scripting
* HTTP Flood
* Scanners and Probes

### [Step 2 - Customising and extending AWS WAF Security Automations Solution](docs/step-2.md)

In step 2 you will customise the rules and settings of the the AWS WAF Security Automation Solution.

### [Step 3 - Optional Extensions](docs/step-3.md)

Step 3 contains two optional extensions to the workshop.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
