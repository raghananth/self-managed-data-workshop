---
title: "Create an ElasticSearch cluster"
date: 2021-04-08T10:00:00-08:00
weight: 50
draft: false
---

### Create the ElasticSearch cluster

Use the CloudFormation template modified earlier to create the ElastiCache cluster.

#### To create the stack

1. In the Cloud9, enter the following command
   ```bash
   echo https://$BUCKET_NAME.s3.amazonaws.com/od4es.json
   ```

1. Browse to the [AWS CloudFormation console](https://console.aws.amazon.com/cloudformation/).
   {{% notice note %}}
   Make sure you are in AWS Region where you will be running the workshop
   {{% /notice %}}

1. Click **Create stack**.

1. In the **Specify template** section, select **Amazon S3 URL**. Enter the value from the first command and click **Next**.

1. In the **Specify stack details** section, enter a **Stack name**. For example, use *ElasticSearchStack*. The stack name cannot contain spaces.

1. In the **Parameters** section, select *elasticsearch* as the **KeyName** parameter.

1. [Optional] In the **Parameters** section, optionally change the *CIDRPrefix* to restrict instance ssh/http access and load balancer http access.

1. Click **Next**. 

1. In **Configure stack options**, you don’t need to make any changes. Click **Next**.

amzn2-ami-hvm-2.0.20201218.1-x86_64-gp2 - ami-03130878b60947df3
Amazon Linux 2 AMI 2.0.20201218.1 x86_64 HVM gp2
Root device type: ebs Virtualization type: hvm ENA Enabled: Yes

1. Review the information for the stack. At the bottom under **Capabilities**, select **I acknowledge that AWS CloudFormation might create IAM resources** and **I acknowledge that AWS CloudFormation might require the following capability: CAPABILITY_AUTO_EXPAND**. When you’re satisfied with the settings, click **Create stack**.

### Monitor the progress of stack creation

It will take roughly NNN minutes for the stack creation to complete.

1. On the [AWS CloudFormation console](https://console.aws.amazon.com/cloudformation/), select the stack in the list.

1. In the **stack details** pane, click the **Events** tab. You can click the refresh button to update the events in the stack creation.

The **Events** tab displays each major step in the creation of the stack sorted by the time of each event, with latest events on top.

The **CREATE_IN_PROGRESS** event is logged when AWS CloudFormation reports that it has begun to create the resource. The **CREATE_COMPLETE** event is logged when the resource is successfully created.

When AWS CloudFormation has successfully created the stack, you will see the **CREATE_COMPLETE** event at the top of the Events tab:

