# Guide to Create and Manage an AWS RDS MySQL Database

## Step 1: Create an AWS RDS MySQL Database in Single AZ

1. Log in to the AWS Management Console.
2. Navigate to RDS.
3. Click "Create database".
4. Choose "MySQL".
5. Select "Full Configuration".
6. Template "Production"
7. Availability and Durability "Single-AZ DB instance deployment (1 instance)"
8. Set DB instance identifier (e.g., mydb).
9. Set Master username and password (Self managed).
10. Choose "Burstable Classes" instance class (e.g., db.t4g.micro).
11. Set storage "General Purpose SSB"(e.g., 20 GB).
12. Configure VPC, subnet group, etc.
13. Public access "Yes"
14. Click "Create database".

## Step 2: Connect to the Database

1. Get the endpoint from RDS console.
2. Use MySQL client: `mysql -h <endpoint> -u <username> -p`
3. Enter password.

**Note** Modify the Security to allow access. 

## Step 3: Create a Database and Table, Populate Records

1. Create database: `CREATE DATABASE devops_class_db;`
2. Use database: `USE devops_class_db;`
3. Create table: `CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(100), email VARCHAR(100));`
4. Populate 100 records (example script):
   ```sql
   INSERT INTO users (name, email) VALUES
   ('User1', 'user1@example.com'),
   ('User2', 'user2@example.com'),
   -- Repeat for 100 records
   ;
   ```
   (Use a loop or script to generate 100 inserts.)


## Step 4: Reboot with Multi-AZ Failover

1. Select your instance.
2. Click "Actions" > "Reboot".
3. Check "Reboot with failover?".
4. Click "Confirm".

## Step 5: Modify to Multi-AZ

1. In RDS, select your instance.
2. Click "Modify".
3. Under Availability & durability, select "Create a standby instance" (Multi-AZ).
4. Click "Continue".
5. Choose "Apply immediately".
6. Click "Modify DB instance".


## Next step - hosting the instance on an AWS Ubuntu EC2 instance. 