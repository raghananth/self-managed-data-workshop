---
title: "Setup the workshop"
date: 2021-04-08T10:00:00-08:00
weight: 30
draft: false
---

### Create a Cloud9 environment

AWS Cloud9 comes with a terminal that includes sudo privileges to the managed Amazon EC2 instance that is hosting your development environment and a preauthenticated AWS Command Line Interface. This makes it easy for you to quickly run commands and directly access AWS services.

Create the Cloud9 environment

### Setup region

All of the workshop will be run in a particular region. Set the **REGION** variable to use in further commands.

```bash
export REGION=<your region>
```

### Setup a S3 bucket

The workshop will use CloudFormation templates to create the AWS resources. The CloudFormation templates will be uploaded to this S3 bucket.

```bash
aws s3 mb s3://<your bucket name> --region $REGION
aws s3 ls
```
The last command should display all of the S3 buckets in this region. Set the **BUCKET_NAME** variable to <your bucket name> to use in further commands.

```bash
export BUCKET_NAME=<your bucket name>
```

### Create an SSH key

Generate a key pair and upload it to AWS to access the instances.

1. Run this command to generate SSH Key.
    ```bash
    ssh-keygen
    ```

1. Select *elasticsearch* as the file name.

1. Press enter 2 times to generate the key pair.

1. Upload the public key to your region

```bash
aws ec2 import-key-pair --key-name "elasticsearch" --public-key-material --public-key-material fileb://~/environment/elasticsearch.pub
```

### Clone the github repository

In order to execute the steps in the workshop, you’ll need to clone the workshop GitHub repository. 

Run the following command to clone the required repository:

```bash
git clone https://github.com/senkinnar/opendistro-es-cfn.git
```
