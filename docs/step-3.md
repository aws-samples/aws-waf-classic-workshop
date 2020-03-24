# Step 3 - Optional Extensions

## 3.1 Challenge - Integrate AWS WAF datapoints to AWS Security Hub

* [Enable AWS Security hub](https://console.aws.amazon.com/securityhub/home?region=us-east-1#/onboard)
* Create an automation ([like this one](https://www.imperva.com/blog/imperva-integration-with-aws-security-hub-expanding-customer-security-visibility/)) to ingest AWS WAF Alert to AWS Security Hub. More info about AWS Security Hub custom providers [here](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-custom-providers.html)


## 3.2 Play with the OWASP Juice Shop.

* The sample application you deployed is the OWASP Juice Shop. It intentionally contains common web vulnerabilities. WAF automatically protects against some of these vulnerabilities, such as SQL Injection and Cross Site Scriptting. There is an [accompanying book by Ben Kimminitch](https://bkimminich.gitbooks.io/pwning-owasp-juice-shop/) that explains further. Try exploring the site to test out some other vulnerabilities. Access your EC2 resource directly (bypassing the ALB) to test your attacks without the WAF protection.
