## EBS Volume

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
	* For


* Capacity & Biling


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

Screenshot

#### EBS Snapshots Features
* EBS snapshot Archive
	* Move a Snapshot to an "archive tire" that is 75% cheaper
	* Takes within 24 to 72 hours for restoring the archive
* Recycle Bin for EBS Snapshots
	* Setup rules to retain deleted snapshots to you can recover them after an accidental deletion
	* Speicfy retention (from 1 to 1 year)


