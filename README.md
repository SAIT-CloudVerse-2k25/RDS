# AWS RDS Hands-On Guide

## 1. Prepare Your Environment

- **Platform**: AWS Console + AWS CloudShell
- **Tools Needed**: MySQL client

## 2. Create RDS Database Instance

1. Go to **RDS → Databases → Create Database**

2. Choose:

   - **Standard Create**
   - **Engine**: MySQLfor 
   - **Version**: Latest supported
   - **DB Instance Class**: db.t3.micro (Free Tier)
   - **Storage**: General Purpose SSD (gp2)
   - **VPC**: Select **Default VPC**
   - **DB Subnet Group**: Default
   - **Publicly Accessible**: Yes

   - **Connectivity → VPC Security Group**:
     - Click **Create New Security Group**
     - Name: `mydb-sg`
     - Rule: Add **MySQL/Aurora (3306)** inbound
     - Source: `Anywhere (0.0.0.0/0)`

   - **Master Username**: `admin`
   - **Password**: (choose strong password)

3. Click **Create Database**

4. Wait until status = **Available**

## 3. Connect from CloudShell

1. Copy the **RDS Endpoint** from **Connectivity tab**.  
2. In **CloudShell**, run:  
   ```bash
   mysql -h <RDS-endpoint> -P 3306 -u admin -p

 Enter your password.
 You should see:

    Welcome to the MariaDB monitor...
    MySQL [(none)]>

## 4. SQL Operations

### Step 1: Create Database
```sql
CREATE DATABASE college;
```
### Step 2: Use Database**
```sql
USE college;
```
Step 3: Create Table
```sql
CREATE TABLE students (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(50),
  prn INT
);
```
Step 4: Insert Records
```sql
INSERT INTO students (name, roll_no) VALUES ('Vaishnavi', 48), ('Radhika', 55);
```
Step 5: Retrieve Records
```sql
SELECT * FROM students;
```
Exit MySQL Session
```sql
exit;
```
