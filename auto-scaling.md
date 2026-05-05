# Guide: Create a highly available application deployment with AWS Management Console
# Reference: hosting.md in this folder for application details, VPC/subnet requirements, and instance configuration.

## 1. Review hosting.md
    - Open hosting.md in this folder.
    - Confirm the application port, instance AMI, security group rules, and any user data requirements have been created successfully

## 2. Create a Target Group
    - In the AWS Management Console, go to EC2 > Load Balancing > Target Groups.
    - Choose Create target group.
    - Select Target type: Instances.
    - Protocol: HTTP, Port: 80 (or the port defined in hosting.md).
    - VPC: use the application VPC from hosting.md.
    - Health checks: HTTP, Path: / or the path used by your app.
    - Create the target group.

## 3. Create an Application Load Balancer
    - In EC2 > Load Balancing > Load Balancers, choose Create Load Balancer > Application Load Balancer.
    - Name the load balancer and select internet-facing or internal based on hosting.md.
    - Select at least two availability zones and their public subnets for high availability.
    - Configure security settings and choose or create a security group allowing HTTP/HTTPS traffic.
    - Configure routing: attach the target group created above.
    - Review and create the load balancer.

## 4. Create a Launch Template
    - In EC2 > Instances > Launch Templates, choose Create launch template.
    - Enter a name and description.
    - Choose the AMI and instance type from hosting.md.
    - Add key pair, network settings, and security group consistent with hosting.md.
    - Under Advanced details, add user data to install and start the application if needed.
    - Create the launch template.

## 5. Create an Auto Scaling Group
    - In EC2 > Auto Scaling > Auto Scaling Groups, choose Create Auto Scaling group.
    - Select the launch template created above.
    - Choose the VPC and at least two subnets in different Availability Zones.
    - Set the Group size: minimum 2, desired 2, maximum 4 for a highly available pattern.
    - Attach the Auto Scaling group to the target group created earlier.
    - Configure scaling policies if required, or leave defaults for fixed capacity.
    - Review and create the Auto Scaling group.

## 6. Verify deployment
    - In EC2 > Load Balancing > Load Balancers, select the ALB and verify listeners and target health.
    - In Target Groups, confirm targets are healthy in at least two AZs.
    - In Auto Scaling Groups, confirm instances are running in multiple subnets.
    - Access the load balancer DNS name to confirm the application is reachable.

## Notes
    - Use hosting.md for any application-specific values such as ports, AMI IDs, security group ports, and startup scripts.
    - A highly available pattern requires multiple AZs, a load balancer, and an Auto Scaling group with at least two instances.
