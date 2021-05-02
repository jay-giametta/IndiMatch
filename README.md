# IndiMatch  
**Description**: A personal website project to work through CI/CD and web development fundamentals on AWS  

**The AWS Pipeline**:  
 1. Code is manually uploaded to a 'dev' branch in *CodeCommit*.  
 2. Code is manually reviewed then pulled/merged into a 'stage' branch in *CodeCommit*.  
 3. *CloudWatch* notifies *CodeBuild* when new code hits the 'stage' branch.  
 4. *CodeBuild* automates lint and unit testing (ex. *TaskCat*) using the test buildspecs in this repo.  
 5. *CodePipeline* sends the verified code to *CloudFormation* and *S3*.  
 6. *CloudFormation* builds a Test *EC2* stack using the infrastructure code in this repo.  
 7. *S3* hosts the Ansible playbooks along with the rest of the verified source code in a Test bucket.  
 8. *Systems Manager* baselines the state of the Test *EC2* instance using the Ansible playbooks hosted in *S3* Test bucket.  
 9. Dynamic testing is done using a *Cloud9* IDE terminal connected to the Test *EC2* instance.  
 10. A manual approval is made in *CodePipeline* to verify the Test environment.  
 11. *CodeBuild* merges the 'stage' branch into the 'main' branch in *CodeCommit*.  
 12.  *CodePipeline* sends the verified code to *CloudFormation* and *S3*.  
 13. *CloudFormation* builds a Live*EC2* stack using the infrastructure code in this repo.  
 14. *S3* hosts the Ansible playbooks along with the rest of the verified source code in a Live bucket.  
 15. *Systems Manager* baselines the state of the Live *EC2* instance using the Ansible playbooks hosted in *S3* Live bucket.  

**Other Capabilities**:  
Ansible - Deploy server capabilities to production state from baseline AMI  
Docker - Will host webserver microservice capabilities (No web cape deployed yet)  
Kubernetes - Orchestrates network/reliability capabilities for Docker microservices  
