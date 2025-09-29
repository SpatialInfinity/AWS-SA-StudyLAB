#AWS Certified Solutions Architect Associate Study Notes

## Introduction
These are my study and lab notes for my AWS journey.


## Identity (IAM) & AWS CLI

Identity as a service is a global service. The first indictator to knowing a service is a global service, open the region drop down, if regions  are greyed out. It means the service itself is global. If you can select regions, it is a location based service.

## IAM MFA Overview

### Introduction
MFA offers another layer of security infront of a password. Even if the attacker finds the password, the identity cannot be accessed unless the attacker gets ahold of the users physical device. 

### MFA options
There are several MFA device options such as using a mobile device running a MFA app (Google Authenticator, Authy, etc...) or a universal 2nd factor security key eg. Yubikey by Yubico (supports multiple root and IAM users using a single key). Other MFA options includes hardware key fob by Gemalto or another by Surepass ID for AWS GovCloud. 

### AWS Access Keys, CLI and SDK


### Ways to access AWS
- AWS management console (protected by password + MFA)
- AWS Command Line Interface (protected by access keys)
- AWS SDK (protected by access keys)

Access keys can be generated from the AWS console. Users can manage their own access keys
Access keys are secret, just like a password. They are not to be shared. Access key id = username and Access secret = password

### What is the AWS CLI

AWS CLI tool allows you to interact with AWS services using command line shell. Offers direct access to the public API of AWS services. Scripts can be developed to manage your resources, it is also open source. 

### What is the AWS SDK?

Similar to the AWS CLI, it allows you to access AWS services programmatically. Allows you to embed within your application(s). 
Supported languages Java script, python, php, .net, ruby, java, Go, Nodes.JS, C++
Mobile SDKs (Android, iOS)
IoT devices SDKs (embedded C, Adunino)
AWS CLI was built on AWS SDK for python

### How can users access AWS?

### IAM Guidelines & Best Practices
- Don't use the root account except for AWS account setup
- One Physical user = ONE AWS user eg. Create a unique credential per physical user
- Assign users to groups and assign permission to groups
- Strong PWD policy
- Enforce MFA
- Create roles for permissions to AWS services
- Audit permissions using credential report and IAM access advisor
- never share IAM users and keys

## EC2 Basics

### Configuraiton Options

OS - Linux / Windows / MacO0S
How much Compute power and cores (CPU)
RAM
Storage
  -  Network attached (EBS and EFS) - Readmore
  -  Hardware EC2 instance store
Network Card -  Speed of card / public ip addressing
Firewall Rules - Security group
Bootstrap script: EC2 User data
Possible to bootstrap instances - Launches commands once on start.
Bootstrapping is useful for updating instances

## Security Group

## EC2 - Solutions Architect

### Private vs Public vs Elastic IP
IPv4 allows for 3.7 billion combinations 
IPv6 mainly used for IoT

### Elastic IP
Max 5 per account
Allows for you to quickly reassign IP to a different instance
There is an hourly charge for inuse and idle usage for IPv4 address $0.005
Free tier account allows for 750 hours per months IPv4 address regardless of instance type
Elastic IP is associated with instance id and private ip address

### Placement groups
- Up to 7 partitions per AZ
- Can span across multiple AZs in the same region
- Up to 100s of EC2 instances
- The instances in a partiion do not share racks with the instances in the other partitions
- A partition failure can affect many EC2 but won't affect other partitions
- EC2 stances get access to the partition information as meta data
  Use cases of partitions are big data type of apps such as HDFS HBASE Casanadra and KAFKA

### Practice placement groups
Look into more videos on placement groups and test

### Elastic Network Interfaces (ENI)
- Each ENI can have 1 or more private IPV4
- One Elastic IP (IPV4) per private IPV4
- One Public IPV4
- One or more security groups
- A MAC address
- ENI can be created independently and attach on the fly to other EC2 instances
- Bounded to specific AZ


### EC2 Hibernate
- Supported instances famillies
- EBS volume must be encrypted in order for hibernate to work

Study more on placement groups and EC2 hibernation

## HA and Scalability ELB and ASG

### HA and Scalability 


## EC2 Instance Storage

### What's An EBS Volume?
- An Elastic Block Store which is a network drive
- Allows your data to exist, even after their termination
- They can only be mounted to one instance at a time
- Network Drive -  latency needs to be considered, detachable and mountable to other Instances
- Locks to an AZ - to move volume, you will need to snapshot the volume
- Provisioned capacity ( GBs size and IOPS )
- Billed for all provisioned capacity
- Capacity can be increased
- Cannot be provisioned 2 instances at a time
- An instance can support more than 1 EBS volume
- Delete on terminatin of EC2 can be activated - by default off

### EBS Hands On


### EBS Snapshots

- Not necessary to detach EBS in order to snapshot
- Make backup of EBS volume at a point in time
- Can copy snapshot across AZ or Region
- EBS snapshots can be moved to an archive tier which is 75% cheaper
- 
  

### Snapshot Lab

- During snapshot creation, snapshot can be restored into a different AZ
- Retention rules can be adjusted to prevent accidental deletion.
- To move the snapshot to a different region, a snapshot must be first taken and then copied to the desired region

### AMI Overview

- AMI = Amazon Machine Image
- AMI are a customisation of an EC2 instance, own software, config , etc can be added. Faster boot / config time of all software is pre-packaged.
- AMI built for a specific region (can be copied across regions)
- 


EC2 Instance Store

Since EBS Volumes are network drives, there is latency involved so another way to have high performing storage. A physically attached drive would be the ideal option. Better I/O performance will be seen, EC2 instance store goes offline, if the EC2 instance is stopped. Having an EC2 instance store it is good for buffer / cache / scratch data and temporary content. Risk total data loss if hardware fails. It is most definitely not an ideal option for long term storage

EBS Volume Types

EBS Volumes comes in 6 types
GP2 / GP3 (SSD) - General purpose SSD volume. Price and performance can be balanced - usable as boot volume
io1 / io2 block express (SSD) - Highest performance SSD volume for mission critical, low latency or high throughput type of workloads - usable as boot volume
st I (HDD) - Low cost HDD volume for frequently accessed throughput intensive workloads 
sc 1 (HDD) - lowest cost HDD for low frequency usage

EBS Volumes defined by SIZE / THROUGHPUT  / IOPS (I/O Ops Per Sec)

General Purpose SSD
Cost effective network storage, low latency
1 GB to 16 TB
GP3
Base Line of 3000 IOPS / 125 MiB/s throughput
IOPS up to 16,000 throughput up to 1000 MiB/s
More control
GP2
Small GP2 Volumes, bursts IOPS to 3000
Size of the volume and IOPS are linked, max IOPS is 16,000
2 IOPS per GB at 5334 GB max ops potential
performance varies based on storage level


EBS Volume Types



