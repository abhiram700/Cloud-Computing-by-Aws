This project demonstrates how to implement Blue-Green Deployment using AWS services to ensure seamless application updates with zero downtime. The deployment process leverages EC2 instances, Application Load Balancers, and Target Groups to manage traffic and application updates efficiently.
Overview
Blue-Green Deployment is a strategy to reduce downtime and risk by running two identical production environments, referred to as Blue and Green. Only one of the environments (Blue) is live at a time, while the other (Green) is used for staging the new version of the application. Once the Green environment is tested and verified, the traffic is switched from Blue to Green, making it live without any disruption.

In this project:

AWS EC2 Instances are used to provision application servers.
Target Groups and Application Load Balancers (ALB) manage the traffic.
Server 1 & Server 2 host the live Guardian application (Blue).
Server 3 & Server 4 display a simple "It Works" message, verifying that deployments are successful without affecting service.
Traffic is routed exclusively to Server 1 & Server 2 via the Load Balancer during the live deployment phase, and the Green environment is activated once the deployment is complete.
Architecture
Blue Environment: Active servers (Server 1 & Server 2) running the live application.
Green Environment: Staging servers (Server 3 & Server 4) to verify new deployment updates.
AWS Components:
EC2 Instances: Host the application.
Application Load Balancer: Distributes traffic between the Blue and Green environments.
Target Groups: Group EC2 instances to manage traffic routing.
Project Setup
Prerequisites
AWS Account: You need an AWS account to launch EC2 instances, set up the ALB, and use other AWS services.
AWS CLI: The AWS Command Line Interface can be useful for deployment automation.
Git: Make sure you have Git installed for version control.
Deployment Steps
Create EC2 Instances:

Set up 4 EC2 instances (2 for the Blue environment and 2 for the Green environment).
Configure the EC2 instances to host your application (e.g., deploy the Guardian application on Server 1 & Server 2, and show the "It Works" message on Server 3 & Server 4).
Create Application Load Balancer:

Set up an Application Load Balancer in AWS to manage traffic between the Blue and Green environments.
Create two Target Groups: one for the Blue environment (Server 1 & Server 2) and one for the Green environment (Server 3 & Server 4).
Configure the Load Balancer to route traffic to the Blue environment during initial deployment.
Blue-Green Deployment Strategy:

Deploy the Guardian application to the Green environment (Server 3 & Server 4).
Once the deployment is verified, switch the traffic routing to the Green environment via the Load Balancer.
Testing:

Test the Green environment to ensure the new version is deployed correctly.
Once verified, route production traffic to the Green environment, ensuring zero downtime for end-users.
Post-Deployment
Once the Green environment is active, monitor application performance using AWS CloudWatch to ensure everything functions as expected.
You can later switch back to the Blue environment if needed.
Technologies Used
AWS EC2: For provisioning and managing virtual servers.
AWS ALB (Application Load Balancer): For routing traffic to the correct environment.
AWS Target Groups: For managing and directing traffic to the right set of EC2 instances.
AWS CloudWatch: For monitoring the deployment and performance of the application.
Conclusion
By using AWS to implement a Blue-Green Deployment strategy, this project demonstrates how to manage application updates safely with zero downtime. This approach helps to ensure high availability, efficient traffic management, and smooth application updates without affecting user experience.
