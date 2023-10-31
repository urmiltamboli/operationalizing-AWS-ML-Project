# Operationalizing-AWS-ML-Project

## Training and deployment

For this training and deployment, ml.t3.medium instance is created as it is included in the free tier and the we are just using it to run the notebook as the training will be on the much powerfull instance. We do not need much computational power while running the notebook so i believe this is the best economical and effiencent instance.

![Notebook Instance](instance.png)

Data is downloaded into the created bucket as below:

![s3 Bucket](s3_bucket_main.png)

![s3 Bucket](s3_bucket.png)


Below is the snap of the deployed endpoint from the inference. Two endpoints are deployed, one with single instance and one with multi instance

![Deployed Endpoint](endpoint2.png)

## Training and deployment using EC2

In this case we have used t3.2xlarge instance which is more powerful as the model will be trained on this instance unlike the notebook. We need a good high power instance to be able to finish the training job in an acceptable timeframe. 

![EC2 Instance](ec2_ins.png)

 Below is the output of the output of the training from the EC2

![EC2 Training Output](ec2.png)

 ## Lambda function setup and security

 Below is the lambda function setup giving IAM access to the role and deploying the python file

![IAM Security](iam_sec.png)

 Below is the output from when testing the lambda function

![Lambda Function Response](lambda_func.png)


 ## Concurrency

 We have reserved 2 Provisional concurreny for this lambda. This type would generate high cost as per our requirement. 

![Concurrency](concurrency.png)

 We have also set up autoscaling for our endpoint in Sagemaker. We have set 3 instance with the cool down period of 30 second for both scale in and scale down. This helps with low latency and also help with cost as if there are no request, it will be off after 30 seconds. 

 Below is the snap of the autoscaling paramters.

 ![Autoscaling Params](auto_sclaing_param.png)

 ![Auto Scaling Deployed](autoscaling.png)
