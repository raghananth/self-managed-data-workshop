---
title: "Setup the ElasticSearch CloudFormation scripts"
date: 2021-04-08T10:00:00-08:00
weight: 40
draft: false
---

### Review the CloudFormation scripts

The github clone downloads CloudFormation templates to create the ElasticSearch cluster.

#### od4es.json
This is the root stack, that you deploy directly via the CloudFormation console. It contains links to the other stacks that will create a VPC, create a seed node for bootstrapping an ES 7 cluster, create master nodes, create data nodes, and create a client node with a public IP address.

#### network.json
Deploys an Amazon VPC to provide secure networking for the Open Distro for Elasticsearch cluster. The VPC spans 2 availability zones, with a public and a private subnet in each of those zones. The stack adds an Internet Gateway for outbound traffic and a NAT gateway for inbound traffic. EC2 instances in the public subnet can have public IP addresses; the seed node, and the client nodes are publicly accessible.

#### seed.json
Deploys a single, seed instance at a known IP address that is the seed to bootstrap the Elasticsearch cluster.

#### data-nodes.json
Deploys an auto scaled group of data nodes into the private subnet of the VPC

#### master-nodes.json
Deploys an auto scaled group of master nodes. Initially it deploys 2 instances. The seed node remains in the cluster as the 3rd master.

##### client-nodes.json
Deploys an auto scaled group of client nodes with public IP addresses in the public subnet of the VPC. These instances also join the cluster as client nodes. The client nodes run Kibana server.

### Get AMI

The CloudFormation templates to create Seed, Master, Client and Data nodes use the Amazon Linux 2 AMI to create the instances. The AMI in the scripts needs to be updated with the latest version of Amazon Linux 2.

Find the latest Amazon Linux 2 AMI and set the **LINUX_2_AMI** variable to use in further commands.

```bash
export LINUX_2_AMI=$(aws ec2 describe-images \
    --owners amazon \
    --filters "Name=name,Values=amzn2-ami-hvm-2.0.????????.?-x86_64-gp2" "Name=state,Values=available" \
    --query "reverse(sort_by(Images, &Name))[:1].ImageId" \
    --output text)
```

### Update the root CloudFormation template

The root CloudFormation template will be updated with the correct region and S3 location for the nested scripts. Run the following command to:

* point the template to <your region>.
* point the template to the S3 location for the nested templates.

```bash
cd opendistro-es-cfn
sed -i.bak -e "s/us-west-1/$REGION/g" -e "s/aws-es-demo/$BUCKET_NAME/g" od4es.json 
```

### Update the nested CloudFormation template

The seed, client, master, and data CloudFormation templates will be updated with the correct region and latest Amazon Linux 2 AMI. Run the following command to:

* point the templates to <your region>.
* point the templates to the latest Amazon Linux 2 AMI in your region.

```bash
sed -i.bak -e "s/us-west-1/$REGION/g" -e "s/ami-03130878b60947df3/$LINUX_2_AMI/g" client-nodes.json data-nodes.json master-nodes.json seed.json
```

### Upload the CloudFormation templates to S3

The edited CloudFormation templates will be uploaded to the S3 bucket created earlier.

```bash
aws s3 rm s3://$BUCKET_NAME/ --recursive --exclude "*" --include "*.json"
aws s3 cp . s3://$BUCKET_NAME/ --recursive --exclude "*" --include "*.json" 
```

