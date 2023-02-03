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

  ### To decode "`Encoded authorization failure message`"

  - When you run API calls and they fail, you can get a long error message.
  - This error message can be decoded using the STS command.
    ```
    aws sts decode-authorization-message --encoded-message <value>
    ```

  ### EC2 Instance Metadata

  - AWS EC2 Instance Metadata is powerful but one of the least known features to developers
  - It allows AWS EC2 instances to ”learn about themselves” without using an IAM Role for that purpose.
  - The URL is http://169.254.169.254/latest/meta-data
  - You can retrieve the IAM Role name from the metadata, but you CANNOT retrieve the IAM Policy.
  - Metadata = Info about the EC2 instance
  - Userdata = launch script of the EC2 instance
    ```
    curl http://169.254.169.254/latest/meta-data/
    ```

  ### Manage mutiple AWS accounts i.e. create a new profile

  - Go to AWS directory and view profiles/accounts available

  ```
  cd ~/.aws
  ll
  cat credentials
  ```

  - configure/re-configure my default profile

  ```
  aws configure
  ```

  - configure a new profile/account

  ```
  aws configure --profile <name of profile>
  ```

  - to switch to new profile, otherwise, default profile is used

  ```
  aws <service> <action> --profile <name of the profile>
  ```
