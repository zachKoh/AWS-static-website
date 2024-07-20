# Host a Static Website on AWS

This project demonstrates the deployment of a static HTML web app on AWS using a range of AWS services and infrastructure components to ensure security, scalability, and reliability. Below are the detailed steps and configurations used to achieve this.

## Infrastructure Setup

1. **Configured a Virtual Private Cloud (VPC)**:
   - Created a VPC with both public and private subnets across two different availability zones.

2. **Deployed an Internet Gateway**:
   - Facilitated connectivity between VPC instances and the wider Internet.

3. **Established Security Groups**:
   - Implemented security groups as a network firewall mechanism to control inbound and outbound traffic.

4. **Leveraged Two Availability Zones**:
   - Enhanced system reliability and fault tolerance by using multiple availability zones.

5. **Utilized Public Subnets**:
   - Deployed infrastructure components like the NAT Gateway and Application Load Balancer in public subnets.

6. **Implemented EC2 Instance Connect Endpoint**:
   - Enabled secure connections to assets within both public and private subnets.

7. **Positioned Web Servers (EC2 instances) in Private Subnets**:
   - Enhanced security by placing web servers in private subnets.

8. **Enabled Internet Access via NAT Gateway**:
   - Allowed instances in both the private application and data subnets to access the Internet through the NAT Gateway.

9. **Hosted the Website on EC2 Instances**:
   - Deployed the static website on EC2 instances.

10. **Employed an Application Load Balancer**:
    - Distributed web traffic evenly to an auto-scaling group of EC2 instances across multiple availability zones.

11. **Utilized an Auto Scaling Group**:
    - Managed EC2 instances automatically to ensure website availability, scalability, fault tolerance, and elasticity.

12. **Stored Web Files on GitHub**:
    - Used GitHub for version control and collaboration on web files.

13. **Secured Communications Using Certificate Manager**:
    - Ensured secure application communications by using AWS Certificate Manager.

14. **Configured Simple Notification Service (SNS)**:
    - Set up SNS to send alerts about activities within the auto-scaling group.

15. **Registered Domain Name and Configured DNS Record**:
    - Used Route 53 to register the domain name and set up the DNS record.

## Deployment Script

The following Bash script was used to deploy the web application on an EC2 instance:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su

# Update all installed packages to their latest versions
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the current working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws

# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd

# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

## Reference Diagram and Scripts

The reference diagram and scripts used for this deployment are available in the GitHub repository for this project. You can access them [here](https://github.com/aosnotes77/host-a-static-website-on-aws).

## Conclusion

By following the above steps, you can set up a secure, scalable, and reliable static website on AWS. This setup leverages various AWS services to ensure high availability and fault tolerance, making it an ideal solution for hosting static web applications.
