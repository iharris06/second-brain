 # Push Commands
Make sure that you have the latest version of the AWS CLI and Docker installed. For more information, see [Getting Started with Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/getting-started-cli.html) .

Use the following steps to authenticate and push an image to your repository. For additional registry authentication methods, including the Amazon ECR credential helper, see [Registry Authentication](https://docs.aws.amazon.com/AmazonECR/latest/userguide/Registries.html#registry_auth) .

- Retrieve an authentication token and authenticate your Docker client to your registry. Use the AWS CLI:
    
    `aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 610094615449.dkr.ecr.us-east-2.amazonaws.com`
    
    Note: If you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.
    

- Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions [here](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html) . You can skip this step if your image is already built:
    
    `docker build -t learnai-kokoro-tts .`
    

- After the build completes, tag your image so you can push the image to this repository:
    
    `docker tag learnai-kokoro-tts:latest 610094615449.dkr.ecr.us-east-2.amazonaws.com/learnai-kokoro-tts:latest`
    

- Run the following command to push this image to your newly created AWS repository:
    
    `docker push 610094615449.dkr.ecr.us-east-2.amazonaws.com/learnai-kokoro-tts:latest`
# ARN
lambda role: arn:aws:iam::610094615449:role/learnai-tts-lambda-role
synology role: arn:aws:iam::610094615449:user/learnai-webapp
