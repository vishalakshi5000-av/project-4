# Deva AWS CI-CD

**CI-CD Flow in AWS:**
![image](https://github.com/Devakumaran13/aws-deploy/assets/85147601/0f608881-c422-464c-abc0-63143b70f678)

1) Code Setup in AWS Code Commit and GITHUB.
2) Create the required IAM roles.
3) Create the ECR Registory
4) Create the Code Build project
5) Creating the Infra using Cloud Formation
6) Creat the ECS Cluster and define the task and services.
7) Create the CI-CD Pipeline using Code Pipeline.


**1) Code Setup in AWS Code Commit and GITHUB.**

![image](https://github.com/Devakumaran13/aws-deploy/assets/85147601/6413ee22-a002-49ea-9bd3-4751ed49badd)

	--> Create the Code Commit Repo "springboot"
	--> Upload the all required file into repo.

**2) Create the required IAM roles**
	--> Create the IAM User with below permission
		"Amazon ECS Full Access"
		"AWS Code Commit Full Access"
		"AWS Code Commit Power user"
		"Admin Access" if need
	--> Create the HTTPs Git credentials for AWS Code Commit
 
**3) Create the ECR Registory**
![image](https://github.com/Devakumaran13/aws-deploy/assets/85147601/ab52f6f7-5f8f-42d1-b817-6df410c06c74)

	--> Create the ECR Registry private registry.
	--> Copy the ECR URI and past the code commit buildspec.yaml file

**4) Create the Code Build project**
	--> Create the Code Build Project.
	--> Copy the ECR URI and past the code commit buildspec.yaml file
 
**5) Creating the Infra using Cloud Formation**
--> Create VPC and Infra using the "Cloud Formation".

--> aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name ecs-core-infrastructure --template-body file://./core-infrastructure-setup.yml

**6) Creat the ECS Cluster and define the task and services.**
	--> Create the ECS Cluster with name and AWS Fargate (serverless) option.
	--> Create the Task defination with default template value.
	--> Set up Container ports, Image URI and Health check.
		CMD-SHELL, curl -f http://localhost:8080/actuator/health || exit 1
	--> Go to the Service and create the Service using Launch type and Forgate option.
	--> Copy the public IP for task and hit in local host "http://<public_ip>:8080/demo/data"


![image](https://github.com/Devakumaran13/aws-deploy/assets/85147601/97daa4d4-9bf1-4ad8-b39f-852552c2d1ed)

![image](https://github.com/Devakumaran13/aws-deploy/assets/85147601/6b144d69-68d0-402a-926a-fc18388b1890)


**7) Create the CI-CD Pipeline using Code Pipeline.**
![image](https://github.com/Devakumaran13/aws-deploy/assets/85147601/bb02b107-3f89-45e6-9e5c-f75d0ef0dd6f)

	--> Build and Deploy
# springboot-aws-deploy

This is a sample microservice to deploy it on AWS ECS.

To build automated AWS CodePipeline and deploy microservice to AWS ECS, follow tutorial as shown in video :

Video Link :https://youtu.be/ARGmrYFfv44

Health Check command for AWS Task definition : 
```
CMD-SHELL,curl -f http://localhost:8080/actuator/health || exit 1
```


Prerequisite :
1. AWS acconunt.
2. Git and docker installed on the machine.
3. Docker should be started before building docker image.
4. And your favourite code editor 

