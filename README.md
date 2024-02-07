# Azure Database Migration

## Overview
This project aims to architect and implement a cloud-based database system on Microsoft Azure, showcasing expertise in cloud engineering. The primary objectives include establishing a production environment database, migrating it to Azure SQL Database, simulating disaster recovery scenarios, implementing security measures, and setting up a Windows Virtual Machine (VM) to serve as the cornerstone of the production environment.

## Milestone 1
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