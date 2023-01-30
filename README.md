# AWS Certified Developer Associate Codes
All the relevant codes from [Udemy course](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/) to be used for the [AWS Developer Associate Certified certification](https://aws.amazon.com/certification/certified-developer-associate/).

## SSH Mac/Linux CLI
- cd into local folder containing key pair (e.g. EC2Tutorial.pem)
```
chmod 0400 EC2Tutorial.pem
ssh -i EC2Tutorial.pem ec2-user@<Public IPv4 address of your instance>
```

- check version of AWS
```
aws --version
```
- check list of users (need to assign IAM role first)
```
aws iam list-users
```

