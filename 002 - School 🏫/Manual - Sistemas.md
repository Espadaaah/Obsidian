1. [Pfsense](#Pfsense)
	- [Install](#Install)
	- [Web Configurated](Manual%20-%20Sistemas.md#Web%20Configurated)
	- [Certificates](#Certificates)
	- [VPN SITE-TO-SITE](#VPN%20SITE-TO-SITE)
2. [Windows Server](#Windows%20Server)
	- [Install](#Install)
	- [DHCP](#DHCP)
	- [DNS](#DNS)
	- [WDS (windows deployment service)](#WDS%20(windows%20deployment%20service))
	- [GPO’S](#GPO’S)
	- [DPM / MYSQL](#DPM%20/%20MYSQL)
3. [Ubuntu Server (minimized)](#Ubuntu%20Server%20(minimized))
	- [Install](#Install)
	- [IP STATIC](#IP%20STATIC)
	- [DHCP](#DHCP)
	- [DNS](#DNS)
	- [Script Failover](#Script%20Failover)
	- [Cockpit](#Cockpit)
	- [UFW](#UFW)
	- [Postfix](#Postfix)
	- [AD - Ubuntu](#AD%20-%20Ubuntu)
	- [Samba](#Samba)
	- [VSFTP](#VSFTP)
	- [VOIP](#VOIP)
4. [Red Hat Server](#Red%20Hat%20Server)
	- [Zabbix](#Zabbix)
5. [Windows Client](#Windows%20Client)
	- [Install](#Install)
6. [Ubuntu Client](#Ubuntu%20Client)
	- [Install](#Install)
7. [Kali Linux](#Kali%20Linux)
	- [Install](#Install)
---
<br>
<br>
<br>


# Pfsense 
## Install
![](../../attachments/1%20-%20Pfsense%20Installation.png)
![](../../attachments/Untitled.png)
![](../../attachments/Untitled-1.png)
![](../../attachments/Manual%20-%20Sistemas.png)
![](../../attachments/Manual%20-%20Sistemas-1.png)
![](../../attachments/Manual%20-%20Sistemas-2.png)
![](../../attachments/Manual%20-%20Sistemas-3.png)
![](../../attachments/Manual%20-%20Sistemas-4.png)
![](../../attachments/Manual%20-%20Sistemas-5.png)
![](../../attachments/Manual%20-%20Sistemas-6.png)
## Web Configurated
-> _Do this after [Windows Server](#Windows%20Server) INSTALLATION and CONFIGURATION_
![](../../attachments/Manual%20-%20Sistemas-7.png)
![](../../attachments/Manual%20-%20Sistemas-8.png)
-> _Next page (Wan Interface) final the page before NEXT, uncheck these two boxes_
![](../../attachments/Manual%20-%20Sistemas-9.png)
![](../../attachments/Manual%20-%20Sistemas-10.png)
-> _Next page password you choose_
-> _Create Port Forward for email server_
- _To receive mails from outside of our Lan Network._
![](../../attachments/Manual%20-%20Sistemas-11.png)
![](../../attachments/Pasted%20image%2020250711220450.png)
-> _Save and apply changes_
-> _Do the same for SMTP_
![](../../attachments/Manual%20-%20Sistemas-13.png)
-> _Now do rule for permit ping between kali and pfsense_
![](../../attachments/Manual%20-%20Sistemas-14.png)
![](../../attachments/Manual%20-%20Sistemas-15.png)
-> _It will look like the image_
![](../../attachments/Manual%20-%20Sistemas-16.png)
-> _In kali linux do this – like the image_
![](../../attachments/Manual%20-%20Sistemas-17.png)
## Certificates
-> _Make snapshot of pfsense before do this_
![](../../attachments/Manual%20-%20Sistemas-18.png)
![](../../attachments/Manual%20-%20Sistemas-19.png)
![](../../attachments/Manual%20-%20Sistemas-20.png)
![](../../attachments/Manual%20-%20Sistemas-21.png)
-> _Export booth certificates_

-> _Install certificates in trusted root certificates authorit_

-> _Change http to https in pfsense web - (system – Advanced) and change port to another you don’t used.)_

-> _Gpo for certificates_
![](../../attachments/Manual%20-%20Sistemas-22.png)
-> _Import certificate in ubuntu client_
-> _Settings – corticates_
-> _LDAP_
![](../../attachments/Manual%20-%20Sistemas-23.png)
![](../../attachments/Manual%20-%20Sistemas-24.png)
-> _Bind credentials you get in users and computers and go to proprieties of administrator user and attributer editor is here you get this_
-> _è Create group: pfsense-admin and add the domains – like the image_
## VPN SITE-TO-SITE


---
# Windows Server
## Install
## DHCP
## DNS
## WDS (windows deployment service)
## GPO’S
## DPM / MYSQL

---
# Ubuntu Server (minimized)
## Install
## IP STATIC
## DHCP
## DNS
## Script Failover
## Cockpit
## UFW
## Postfix
## AD - Ubuntu
## Samba
## VSFTP
## VOIP

---
# Red Hat Server
## Zabbix

---
# Windows Client
## Install

---
# Ubuntu Client
# Install

---
# Kali Linux
## Install