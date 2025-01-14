+++
title = "e. Set up Compute Environment"
date = 2019-09-18T10:46:30-04:00
weight = 50
tags = ["tutorial", "install", "AWS", "batch", "packer"]
+++

In this step, you will set up an AWS Batch "Compute Environment" using the AWS Management Console.

Compute environments can be thought of as computational clusters consisting of one or more EC2 instance types, or simply as the number of cores you want to use to run your jobs. For more information on the compute environments, see [Compute Environments](https://docs.aws.amazon.com/batch/latest/userguide/compute_environments.html).

1. In the AWS Management Console, in the search bar, search for and choose [**Batch**](https://console.aws.amazon.com/batch/home).  
2. In the left pane, choose **Compute environments**, then choose **Create**.
![AWS Batch](/images/aws-batch/compute-env-1.png)
3. Under **Compute environment configuration**, choose **Managed** for **Compute environment type**. This option allows AWS Batch manage the automatic scaling of EC2 resources for you.  
4. For **Compute environment name** type **stress-ng-ec2**.

5. Check **Enable compute environment**. This option enables the AWS Batch environment when it's ready.
6. Click **Additional settings** and for **Service role**, choose **Batch service-linked role**. The role allows the AWS Batch service to make calls to the required AWS API operations on your behalf. For more information, see [**Using Service-Linked Roles**](https://docs.aws.amazon.com/batch/latest/userguide/using-service-linked-roles.html). For **Instance role** choose **ecsInstanceRole**.
 
7. Under **Instance configuration**, choose **On-demand** for **Provisioning model**. This option allows EC2 to create resources for you as required.

![AWS Batch](/images/aws-batch/compute-env-2.png)

8. Leave the default value of **0** for **Minimum vCPUs**. This allows your environment to scale down to zero instances when there are no jobs to run.
9. For **Maximum vCPUs** type **256**. This is the upper bound for vCPUs across all concurrently running instances.
10.  Leave the default value of **0** for **Desired vCPUs - *optional***.
11.  For **Allowed instance types**, leave the selection as **optimal**.
12.  Select **BEST_FIT_POGRESSIVE** for **Allocation strategy**
![AWS Batch](/images/aws-batch/compute-env-3.png)
13. Under Networking, for **VPC ID**, choose the Default VPC.
14. Select all the subnets.
15. For **Security groups**, select the default.
16. For **Placement groups - *optional***, leave it empty.
![AWS Batch](/images/aws-batch/compute-env-4.png)
17. Under **EC2 tags - *optional***, Add a **Tag** called **Name** and for **Value**, type **stress-ng Batch** as a name for your instances created with Batch. You can add additional tags if you want.
18. Choose **Create compute environment** to build your new compute environment.
19. Once the environment is ready, it will be visible under **Compute environments** section. Make sure *Status* is **VALID** and *State* is **ENABLED**.
![AWS Batch](/images/aws-batch/compute-env-5.png)

At this point, you have done the hard part! Continue to the next step toset up a job queue.



