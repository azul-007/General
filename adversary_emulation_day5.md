## What is Azure Active Directory pg. 4

A cloud service provided by Microsoft to support identity and access management integrated into several cloud services such as Azure and Office 365 applications.

## Azure AD Attack Strategies: Reconnaissance pg. 18

Using Azure AD allows an adversary to perform reconnaissance: Creating an O365 or Azure AD tenant automatically creates a domain <tenant name>.onmicrosoft.com.
Custom domains can also be added to your tenantl owner validation is done via dedicated DNS records.
  
Adveraries will request these DNS records and try to identify the information contained in the TXT or MX records. Microsoft has 2 options to perform domain validation,
where you as an organization need to change your DNS settings with your registrar:

1 - A TXT record that has the value of MS=<random number> with a TTL of 3600 seconds
  
2 - A MX record with a very high priority, destination of the MX record ms <random number>.msv1.invalid with a TTL of 3600 seconds


## Password Spraying pg. 19

Cloud environments are excellent targets for password spraying attacks due to their public logon portals. These types of attacks use a limited set of common 
passwords against many users within the Azure AD tenant. 

During a password spray attack, the malicious actor is going to try a limited set of commonly used passwords against many accounts before moving on to attempt 
a second password. This technique allows the actor to remain undetected by avoiding rapid or frequent account lockouts.

## Password Spraying Tools pg. 20
- Ruler: a tool that allows you to interact with Exchange servers remotely, through either the MAPI/HTTP or RPC/HTTP protocol
- SprayingToolkit: a set of Python scripts that try password spraying attacks against Lync/S4B & OWA
- MailSniper: PowerShell tool for password spraying, enumerating users/domains, gathering the Global Address List from OWA and EWS, and checking mailbox permisssions.

