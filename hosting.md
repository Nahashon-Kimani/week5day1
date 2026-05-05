# Hosting index.php on AWS EC2 with Ubuntu and Apache2

## Step 1: Launch an EC2 Instance
- Go to AWS Management Console.
- Launch an EC2 instance with Ubuntu Server (e.g., Ubuntu 24.04 LTS).
- Configure security group to allow SSH (port 22) and HTTP (port 80).
- Download the key pair (.pem file).

## Step 2: Connect to the Instance
- Use SSH to connect: `ssh -i your-key.pem ubuntu@your-instance-public-ip`

## Step 3: Update the System
- Run: `sudo apt update && sudo apt upgrade -y`

## Step 4: Install Apache2
- Run: `sudo apt install apache2 -y`
- Start and enable: `sudo systemctl start apache2 && sudo systemctl enable apache2`

## Step 5: Install PHP
- Run: `sudo apt install php libapache2-mod-php php-mysql -y`
- Restart Apache: `sudo systemctl restart apache2`

## Step 6: Upload index.php
- Modify the **Amazon RDS MySQL connection settings** in the index.php file. 
- Upload and place the index.php file in `/var/www/html/` in the EC2 instance created above. 
- Example: Use SCP or SFTP to upload.

## Step 7: Set Permissions
- Run: `sudo chown -R www-data:www-data /var/www/html/`
- Run: `sudo chmod -R 755 /var/www/html/`

## Step 8: Access the Site
- Open a browser and go to `http://your-instance-public-ip`
- Your index.php should load.


## Step 9 - Creating an AMI
- Go to the AWS EC2 Dashboard.
- Select your running EC2 instance.
- Click on "Actions" > "Image and templates" > "Create image".
- Enter a name and description for your AMI.
- (Optional) Choose whether to reboot the instance.
- Click "Create image".
- Your AMI will appear under the "AMIs" section once the process is complete.
- Add tags (e.g. Key: Name, Value: PHPWebsite)