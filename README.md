Project 1: Deploy a Scalable Web Application on EC2
This is the foundational "classic" cloud deployment project. You'll build a resilient, scalable infrastructure for a standard web application and automate its entire deployment process.
Architecture
The application servers will be in private subnets, inaccessible from the internet directly. An Application Load Balancer (ALB) in public subnets will be the single entry point, distributing traffic to the EC2 instances. A NAT Gateway allows instances in the private subnet to access the internet for updates.
•	Git: Manages the source code for a simple web app (e.g., Python/Flask).
•	Terraform: Provisions the entire cloud infrastructure as code.
•	Ansible: Configures the EC2 instances by installing a web server and deploying the application code.
•	Jenkins: Automates the pipeline from code commit to deployment.
•	AWS: VPC, EC2, Auto Scaling Group, ALB, S3 (for artifacts).
Step-by-Step Process
1.	Code Setup (Git): Create a simple "Hello World" web app in Python or Node.js. Initialize a Git repository and push it to GitHub/GitLab.
2.	Infrastructure (Terraform): Write Terraform files to create the VPC, public/private subnets, Internet Gateway, NAT Gateway, Security Groups, a Launch Template for EC2, an Auto Scaling Group, and an Application Load Balancer. Define an S3 bucket to store build artifacts.
3.	Configuration (Ansible): Create an Ansible Playbook to install Nginx, download the application artifact from S3, unzip it, and configure Nginx to serve the app.
4.	Automation (Jenkins): Set up a Jenkins pipeline (Jenkinsfile) that:
o	Checks out code from Git.
o	Builds the application (e.g., zips the code).
o	Uploads the artifact to the S3 bucket.
o	Triggers the Ansible playbook to deploy the new artifact onto the EC2 instances.
