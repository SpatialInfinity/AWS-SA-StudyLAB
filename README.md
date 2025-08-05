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







