# Kubernetes/docker integration tests requirements:
## Spin this up with Terraform.
- All v2 services are able to be deployed in docker or via the old BMX way. (For transitional purposes)
- All v2 services are in docker.
- Docker images are built for each branch and put into ECR.
- ECR contains the image for the most recent successfuly build for a branch.
- Kubernetes is able to take designated image and install it on an ec2 (Create new ec2? Reuse?)
- Configuration makes it easy to create deployment groups.
- Configured deployment groups designate the docker images to be deployed.
- Example. Deploy all master branches to the v2 environment.
- Integration testing is done subsequent to kubernetes deploying a v2 group.
- The result of the integration test is made available to the dev team.
- The deployment group can not deploy all master branches unless the master deployment group passes the - integration test.

## Questions:
- How to make it so BMX builds docker image with code base for branch and deploy to ECR instead of deploy to EC2?
- Is it possible to have both ways of deployment working simultaneously in test?
- How to hook kubernetes to draw images from ECR?
### POC (Be able to show):
- Setup cloudwatch alarms on billing for increments of 10$, 20$, 30$ ... 100$. (For my own sake)
- Create 2 helloWorld nodejs projects.
- Spin up ECR and and EKS with terraform, if the items are already there then it does nothing.
- Use Travis CI/CD to build nodejs projects in nodejs docker image and deploy to ECR.
- Connect to EKS from command line.
- Connect to EKS with UI.
- Use Kubernetes to deploy nodejs docker images to ec2 in AWS.
- Be able to spin the nodejs apps up on a timed schedule, be able to do it manually.
- View the nodejs apps running from the kubernetes UI.
- Ensure that the nodejs images in each case are replacing the old ones.
- Be able to easily configure a master deployment group (Only master branches are deployed) or be able to select which branches sepcifically to deploy.
### Extra credit
- Run integrations tests in blue green deployment fashion. They run against eachother only, if they pass then the old containers are torn away and replaced with these ones.
Collapse
