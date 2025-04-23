##  Types of Storage Attached to EC2 Instances
| Types of storage        | Plus point           | 
| ------------- |:-------------:| 
|EBS (Elastic Block Store)|Most common storage. Acts like a network hard disk. Persistent and survives instance stop/restart. Can be detached/attached between instances.
|Instance Store (Ephemeral) |Physical disk attached to the host machine. Very fast, but data is lost if the instance is stopped or terminated.|
|EFS (Elastic File System)|Shared file storage (like a network drive). Accessible from multiple EC2 instances at the same time. Great for shared data or microservices.|
|FSx |High-performance managed file systems (e.g. FSx for Windows, FSx for Lustre) for specific workloads like Windows apps or HPC.|
***
## 1. EBS Volume

### What's an EBS Volume?

##### An EBS(ELastic Block Store) Volume is a network drive you can attach to your instance while they run
* Think of it like :
	* A hard disk attached to your EC2 virtual machine( just like a C: or D: drive on your laptop
	* When your EC2 instance shuts down, the data on EBS remains intact(if not deleted explicitly)
##### It's not physical - it works over the network, so there might be a tiny delay(latency)
##### You can detach it from one EC2 instance and attach it to another, like swapping USB drives
##### It allows your instances to persist data, even after their termination 
##### They can only be mounted to one instance at a time (at the CCP level)
##### They are bound to a specific availability zone

* Availability Zone(AZ) Lock 
	* An EBS volume is locked to one Availability Zone.

	* For example: a volume created in us-east-1a cannot be directly used in us-east-1b.

	* To move it, you need to:

		* Take a snapshot (backup)

		* Create a new volume in the other AZ from that snapshot


* Capacity & Biling
  	* When you create an EBS volume, you choose size (in GB) and optionally IOPS (speed).

	* You pay for the full size you provision — even if you don’t use all of it.

	* You can increase the size later if needed (but not reduce it).


#### EBS Volume - Example

![Screenshot 2025-04-16 203135](https://github.com/user-attachments/assets/596121ee-e609-4d45-94c4-02f4ee0416af)


### Controls the EBS behaviour when an EC2 instance terminates
##### By default, the root EBS volume is deleted ( attribute enabled)
##### By default, any other attached EBS volume is not deleted(attribute disabled)
### This can be controlled by the AWS console/AWS CLI

![image](https://github.com/user-attachments/assets/1a21ad03-09cd-4e0f-8c6d-086aaf7897ab)


#### EBS Snapshots
##### Make a backup (snapshot) of your EBS volume at a point in time
##### Not necessary to detach volume to do snapshot, but recommeded 
##### Can copy snapshots across AZ or Region

![image](https://github.com/user-attachments/assets/32973338-1356-4195-a579-9b4e56340005)


#### EBS Snapshots Features
* EBS snapshot Archive
	* Move a Snapshot to an "archive tire" that is 75% cheaper
	* Takes within 24 to 72 hours for restoring the archive
* Recycle Bin for EBS Snapshots
  	* Recycle Bin protect your Amazon EBS snapshots from accidental deletion (55)
	* Setup rules to retain deleted snapshots to you can recover them after an accidental deletion
	* Speicfy retention (from 1 to 1 year)


### IAM Overview
* AMI = Amazon Machine Image
* An AMI is like a template for EC2 instances.
* It includes:
	* The OS (like Ubuntu, Windows)
	* Your installed software
	* Configurations, settings, etc.
 * Why Use AMIs?
	* You can pre-configure everything so new EC2 instances boot faster.
	* Think of it like a ready-to-use system image
* AMI are a customization of an EC2 instance
  	* You add your own software, configuration, operating system, monitoring...
  	* Faster boot/ configuration time because all your software is pre-packaged
 * AMI are build for specific region (and can be copied across regions)
 * You can launch EC2 instances from:
   	* A public AMI: AWS provided
   	* Your own AMI: you make and maintain them yourself
   	* An AWS Marketplace AMI: an AMI someone else made (and potentially sells)

#### How to Create an AMI
* Launch and customize an EC2 instance
* Stop the instance (for safety)
* Create an AMI from it
* AWS will also take EBS snapshots behind the scenes
* Now you can launch new EC2s from your custom AMI anytime!
![image](https://github.com/user-attachments/assets/1019c27b-78be-4722-b887-9c241fa73dd2)


/-Hands on AMI
***
#### EC2 Image Builder
* used to automated the creation of Virtual Machines or container images
* Automate the creation, maintain, validate and test EC2 AMIs
* Can be run on a schedule(weekly, whenever packages are updated, etc...)
* Free service (only pay for underlying resources)

![image](https://github.com/user-attachments/assets/3fc02910-c03f-44d6-8194-d3bb9527114d)

***
#### 2. EC2 Instance Store
###### EBS volumes are network drives with good "limited" performace
###### If you need a high-performace hardware disk, use EC2 Instance store
###### Better I/O performace
###### EC2 instance store lose their storage if they're stopped (ephemeral)
###### Good for buffer/ cache /scratch data / temporary content
###### Risk of data loss if harware fails
###### Backup and Replication are your responsibility
***
#### 3. EFS - Elastic File System
###### Manged NFS (Netwrok file system) that can be mounted on 100s of EC2
###### EFS works with Linux  EC2 isntances in multi-AZ
###### Highly availabl, scalable, expensive (3x gp2), pay per use, no capacity planning

![image](https://github.com/user-attachments/assets/77dce7ae-6aff-41ba-b395-46f9b6ebb8bb)

### 📦 EBS vs EFS - What's the Difference?

| Feature                | EBS (Elastic Block Store)                                      | EFS (Elastic File System)                                       |
|------------------------|---------------------------------------------------------------|------------------------------------------------------------------|
| 🔗 Attachment          | Attached to **one EC2 instance** at a time                    | Can be attached to **multiple EC2 instances** (shared access)    |
| 💾 Type                | Block Storage (like a hard drive)                            | File Storage (like a network drive)                              |
| 🗃️ Data Access         | One server reads/writes at a time                             | Multiple servers can read/write concurrently                     |
| 🔄 Use Case            | Databases, single-instance applications                      | Shared web content, home directories, microservices              |
| 🌍 Availability Zone   | Locked to **one Availability Zone**                           | Can be accessed across **multiple AZs** in a region              |
| 💡 Persistence         | Persistent across instance stop/start                         | Also persistent and highly

![image](https://github.com/user-attachments/assets/5c29c165-53c3-4f08-aabe-701155b7074a)

### EFS Infrequent Access (EFS-IA)
* Storage class that is cost-optimized  for files not accessed every day
* Up to 92% lower cost compared to EFS Standard
* EFS will automatically move your files to EFS-IA bbased on the last time they were accessed
* Enable EFS-IA with a Lifecycle Policy
* Example: move files that are not accessed for 60 days to EFS-IA
* Transparent to the applications accesssing EFS
![image](https://github.com/user-attachments/assets/63a5c36e-a617-4387-acb1-bef095d83cb7)
### Shared Responsibility Model for EC2 Storage
![image](https://github.com/user-attachments/assets/ff4a59c0-1418-41c7-9bb2-3db1b5358dbb)

***
### 4. Amazon FSx - Overview
##### Launch 3rd party high-performace file system on AWS
##### Fully managed service
* FSx for Lustre
* FSx for Windows File Server
* FSx for NetApp ONTAP

---
* Amazon FSx for Window File Server
  	* A fully managed, highly reliable, and scalable windows nativ shared file system
  	* Build on Windows File  Server
  	* Supports SMB protocol & windows NTFS
  	* Integrated with microsoft Active Directory
  	* Can be accessed from AWS or your on- premise infrastructure
 
  * Amazon FSx for Lustre
    	* A fully anaged, high-performace, scalable fiel storag for High Performace Computing (HPC)
    	* The name Lustre is derived from "Linux" and "cluster"
    	* Machine Learning, Analytics, Video processing, Financial Modeling,...
    	* Scales up to 100s GB/s, millions of IOPS, sub-ms latencies

***
***
# EC2 Instance Storage - Summary

- **EBS volumes**:
  - Network drives attached to one EC2 instance at a time
  - Mapped to an Availability Zone
  - Can use EBS Snapshots for backups / transferring EBS volumes across AZ

- **AMI**: Create ready-to-use EC2 instances with your customizations

- **EC2 Image Builder**: Automatically build, test, and distribute AMIs

- **EC2 Instance Store**:
  - High performance hardware disk attached to your EC2 instance
  - Lost if the instance is stopped / terminated

- **EFS**: Network file system, can be attached to 100s of instances in a region

- **EFS-IA**: Cost-optimized storage class for infrequently accessed files

- **FSx for Windows**: Network File System for Windows servers

- **FSx for Lustre**: High Performance Computing Linux file system


   
