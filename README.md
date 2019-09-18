
### WAF demo prep setup

- create a VPC, add two subnets in two separate AZs
- point an ALB at an AutoScaling Group
- allow http:80 access
- instantiate EC2s with a running webserver


#### deploy

`aws s3 mb s3://$BUCKETNAME`

`aws cloudformation  package  --template-file main.template   --s3-bucket $BUCKETNAME   --s3-prefix stacks   --output-template-file rootstack.json   --use-json   --force-upload`

`aws cloudformation deploy --template-file rootstack.json --stack-name WAFDEMO  --s3-bucket $BUCKETNAME  --s3-prefix stacks && aws cloudformation list-exports --query 'Exports[].{Name: Name, Value: Value}'`

`aws cloudformation delete-stack --stack-name WAFDEMO && rm rootstack.json`


#### todos  
- ssh via system manager
- webserver : restrict ingress and egress to ALB
- cloudwatch dashboard



#### userdata to spin up sample web servers

*httpserver on python2.7:* no special installs  nor updates required, so quick to spin up

```
#!/bin/bash
echo "<h1>Hello AWS WAF Security Automations</h1>" > index.html
python -m SimpleHTTPServer 80 .
```

*default example:* provided by US builders for waf demo
```
sudo yum update -y
sudo yum install -y httpd
sudo systemctl enable httpd
sudo touch /var/www/html/index.html
sudo chmod 666 /var/www/html/index.html
echo "<h1>Hello AWS WAF Security Automations</h1>" > /var/www/html/index.html
sudo systemctl restart httpd
```

*juiceshop:* full fledged vulnerable site

```
#!/bin/bash
yum update -y
yum install -y docker
service docker start
docker pull bkimminich/juice-shop\ndocker run -d -p 80:3000 bkimminich/juice-shop
```
