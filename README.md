# aws-dev-code
All the relevant codes from udemy course to be used for the AWS Developer Associate Certified certification

## SSH Mac/Linux CLI
- cd into local folder containing key pair (e.g. EC2Tutorial.pem)
```
chmod 0400 EC2Tutorial.pem
ssh -i EC2Tutorial.pem ec2-user@<Public IPv4 address>
```

- check version of AWS
```
aws --version
```
- check list of users (need to assign IAM role first)
```
aws iam list-users
```

