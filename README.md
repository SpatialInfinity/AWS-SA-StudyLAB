#AWS Certified Solutions Architect Associate Study Notes

Introduction
These are my study and lab notes for my AWS journey.


Identity (IAM) & AWS CLI

Identity as a service is a global service. The first indictator to knowing a service is a global service, open the region drop down, if regions  are greyed out. It means the service itself is global. If you can select regions, it is a location based service.

IAM MFA Overview

MFA works as a prevention to security compromisation. Even if the attacker finds the password, the identity cannot be accessed unless the attacker gets ahold of the users physical device. There are several MFA device options such as using a mobile device running a MFA app (Google Authenticator, Authy, etc...) or a universal 2nd factor security key eg. Yubikey by Yubico (supports multiple root and IAM users using a single key). Other MFA options includes hardware key fob by Gemalto or another by Surepass ID for AWS GovCloud. 
