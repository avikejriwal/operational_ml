## Notebook instance

I chose the default instance (ml.t3.medium) I don't need a lot of computing power to run the notebook itself. The code can deploy the computiationally intensive parts (such as training the model) to other EC3 instances in SageMaker

## EC2 Instance

The EC2 Instance trains the model directly, rather than creating another instance, so I chose a more powerful instance for model training in this case.  Chose to use an 'm5.xlarge' to this end. Ideally I would use a spot instance, but they weren't available for this setup, so I went with a normal provisioned instance instead.

This is very similar to training the model on SageMaker, except this one is a standalone python script training on a single machine, while SageMaker script focuses on provisioning resources within AWS.

## Lambda Function

The lambda function takes in an parameter for the data to run predictions on and then calls the model endpoint from SageMaker to return a prediction. This is similar to API's that are built in other web applications