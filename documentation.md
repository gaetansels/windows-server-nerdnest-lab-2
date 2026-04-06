## FILESERVER

CONTEXT : 

First, we are going to add a file server to the domain. A file server is a member server in this domain.
A member server is a device that runs the Windows Server software. It is part of the domain, but it is not a domain controller. 
Meaning it has no copy of the Active Directory. 
The file server is connected to the domain because we will configure permissions based on the users in the Active Directory. 

The first thing we are going to do is update the lab environment by adding a member server. 
This is done by adding a full clone to the lab of an already installed Windows server in VMware. 
It can be a full clone because it is a fresh server before configurations, making it easier. 

![something](images/win_lab2_p1.png)

With the following fixed IP (same process lab-1) : 

![something](images/win_lab2_p2.png)

 Next, we are changing the name and adding the file server to the domain (same process lab-1) : 

![something](images/win_lab3_p2.png)

Name File server : FS1 

Note: Due to an incorrect DNS configuration, I could not add my file server to the domain.
This mistake was identified by first testing connectivity using `ping`, which was successful, and then using the command `nslookup nerdnest.test`, which returned a "non-existent domain" error.
Although the server could reach the Domain Controller by IP address, it could not resolve the domain name because the DNS server was incorrectly set to `192.168.153.254` (pfSense), which does not host the Active Directory DNS zone.
After correcting the DNS server to point to the Domain Controller (`192.168.153.220`), the domain name could be resolved and the file server was successfully joined to the domain.
