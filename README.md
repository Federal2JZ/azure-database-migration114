# Azure Database Migration

## Overview
This project aims to architect and implement a cloud-based database system on Microsoft Azure, showcasing expertise in cloud engineering. The primary objectives include establishing a production environment database, migrating it to Azure SQL Database, simulating disaster recovery scenarios, implementing security measures, and setting up a Windows Virtual Machine (VM) to serve as the cornerstone of the production environment.


## Milestone 2 - Setting up the Production Environment
### 1. Provisioning a Windows Virtual Machine (VM)
- **Operating System:** Windows 11 Pro
  - Chose Windows 11 Pro as the operating system for the virtual machine to leverage its advanced features and security enhancements.
- **Virtual Machine Configuration:**
  - Selected appropriate VM size and specifications based on workload requirements and budget constraints.
  - Configured disk size, CPU, memory, and other resources to meet performance needs (Standard D2s v3 (2 vcpus, 8 GiB memory)).
  - Placed the virtual machine within a newly created dedicated resource group for better organisation.
- **Network Configuration:**
  - Configured virtual networking settings to establish connectivity between the VM and other resources in the Azure environment.
  - Implemented firewall rules to control incoming and outgoing traffic, ensuring network security.
- **Remote Desktop Protocol (RDP) Access:**
  - Enabled RDP access to the VM to allow remote management and configuration.
  - Set up secure RDP authentication mechanisms to prevent unauthorised access.

### 2. Establishing Remote Connection
- Established a secure connection to the provisioned VM using the RDP protocol and Microsoft Remote Desktop Connection on a local Windows machine.
- Direct access to the VM's operating system was obtained for efficient management and configuration.

### 3. Installing SQL Server and SQL Server Management Studio (SSMS)
- Installed [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) and [SSMS](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) on the VM to facilitate proficient database management within the production environment.
- Configured SQL Server to ensure optimal performance and security.

### 4. Creating the Production Database
- Restored the AdventureWorks database from the [backup file](https://aicore-portal-public-prod-307050600709.s3.eu-west-1.amazonaws.com/project-files/93dd5a0c-212d-48eb-ad51-df521a9b4e9c/AdventureWorks2022.bak) onto the SQL Server instance on the VM.
- The AdventureWorks database was successfully restored, containing tables, views, stored procedures, and data, emulating a fictional manufacturing company's operations.


## Milestone 3 - Migrating to Azure SQL Database
### 1. Setting Up Azure SQL Database
- Created an Azure SQL Database to serve as the target for migrating the on-premise database.
- Configured SQL login as the chosen authentication method for the associated SQL Server.
- Verified that the SQL Server has appropriate firewall rules, including adding the IP addressof the VM to the firewall settings.

### 2. Preparing for Migration
- Installed and configured Azure Data Studio on the production Windows VM to facilitate database management and migration tasks.

### 3. Connecting to Azure SQL Database
- Used Azure Data Studio to establish a connection to the newly created Azure SQL Database, enabling communication between the on-premise and cloud databases.

### 4. Schema Migration
- Installed the SQL Server Schema Compare extension within Azure Data Studio.
- Leveraged the extension to compare and migrate the schema from the on-premise database to the Azure SQL Database.

### 5. Data Migration
- Installed the Azure SQL Migration extension within Azure Data Studio to facilitate the smooth transfer of data from the on-premise database to the Azure SQL Database.

### 6. Validating Migration Success
- Conducted a comprehensive validation to ensure the success of the database migration process.
- Inspected the migrated database's data, schema, and configurations to confirm adherence to principles of data integrity and successful execution of the migration.


## Milestone 4
### 1. Backup the On-Premise Database
- Generated a full backup of the production database hosted on the Windows VM. This backup essentially duplicates the database, providing a safety net in the event of unforeseen issues.
- Once the backup is complete, stored the resultant backup file in a designated location on the vm or local machine for easy access and redundancy.

### 2. Upload Backup to Blob Storage
- Configured an Azure Blob Storage account, which serves as a secure online repository for your database backups.
- Next, uploaded the previously created database backup file to the Blob Storage container. This step provides an extra layer of backup protection through the presence of a redundant copy stored remotely.

### 3. Restore Database on Development Environment
- To replicate a development environment, provisioned a new Windows VM that mirrored the development setup. Installed SQL Server on this VM to mimic the database infrastructure.
- Subsequently, proceeded to restore the database backup onto this new "sandbox" environment. This allows us to safely explore and experiment with new concepts, while the main production data remains unaffected.

### 4. Automate Backups for Development Database
- On the development Windows VM, utilized SSMS to establish a Management Task that automates regular backups of your development database.
- Configured a weekly backup schedule to ensure consistent protection for the evolving work and simplify recovery for the development environment if needed.