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

## AWS Mac/Linux CLI Dry Runs

- Sometimes, we’d just like to make sure we have the permissions...
- But not actually run the commands!
- Some AWS CLI commands (such as EC2) can become expensive if they
  succeed, say if we wanted to try to create an EC2 Instance
- Some AWS CLI commands (not all) contain a --dry-run option to
  simulate API calls
  ### What is dry run?
  - Checks whether you have the required permissions for the action, without actually making the request, and provides an error response. If you have the required permissions, the error response is DryRun-Operation. Otherwise, it is UnauthorizedOperation .
  - To dry run in attempting to create a new EC2 Instance:

```
aws ec2 run-instances help
aws ec2 run-instances --dry-run --image-id <AMI ID> --instance-type <instance type>
```
