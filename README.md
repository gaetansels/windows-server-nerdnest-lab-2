# windows-server-nerdnest-lab-2
This lab is build upon the "windows-server-nerdnest-lab-1" infrastructure project.  
It focuses on the deployment, configuration, and security of a dedicated Windows File Server.

The lab demonstrates advanced storage management, NTFS permission structures, and File Server Resource Manager (FSRM) implementation.

## Project Context
**NerdNest** is a growing IT service provider. As the organization expands, a centralized, secure, and regulated file storage system is required to handle departmental data while adhering to the **Principle of Least Privilege (PoLP)**.

## Lab Environment
This lab adds a new virtual machine to the existing `gsNerdNest.test` domain environment:

* **File Server:** Windows Server (Member Server)
    * **Static IP:** `192.168.153.221`
    * **Domain:** `nerdnest.test`   
* **Storage:** 100GB secondary virtual disk (NTFS formatted) for departmental shares.

## Key Objectives

### 1. Storage Configuration
* Initialization and formatting of a **100GB virtual disk**.
* Implementation of the **NTFS** file system to support advanced security descriptors and quotas.

### 2. Departmental Folder Structure & AGDLP
The file system is structured based on the company's organogram (HR, IT, Software Development, Accounting, Marketing & Sales, and Operations). Permissions are managed using the **AGDLP** (Accounts, Global Groups, Domain Local Groups, Permissions) strategy:
* **Scalability:** Permissions are assigned to Domain Local groups, not individual users.
* **Global Groups:** Users are organized by department and role.
* **Special Access:** Implementation of cross-departmental access (e.g., HR access to Financial docs) and Full Control for the IT department.

### 3. File Server Resource Manager (FSRM)
To ensure system stability and policy compliance, the following restrictions were implemented:
* **File Screening:** Users are blocked from saving video files to the server to preserve bandwidth and storage.
* **Storage Quotas:** A hard limit of **100MB** per user to prevent storage exhaustion in this test environment.

## Scenario Testing
The configuration is validated by logging in as **Emma De Ridder** (Operations) to verify:
* Read/Write access to all shared folders as per administrative requirements.
* Successful blocking of large file transfers/video files.
* Verification of the 100MB quota limit.

---
*Note: This lab is part of the Graduaat Systeem- en Netwerkbeheer (Course: Windows Server Intro) at Howest Brugge.
