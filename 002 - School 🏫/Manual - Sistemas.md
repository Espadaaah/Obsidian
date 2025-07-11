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



## Web Configurated

## Certificates
-> _Make snapshot of pfsense before do this_
](../../attachments/Manual%20-%20Sistemas-19.png)
![](../../attachments/Manual%20-%20Sistemas-20.png)
![](../../attachments/Manual%20-%20Sistemas-21.png)
-> _Export CA_

-> _Install certificates in trusted root certificates authorit_
![](../../attachments/Manual%20-%20Sistemas-35.png)
![](../../attachments/Manual%20-%20Sistemas-36.png)
![](../../attachments/Manual%20-%20Sistemas-37.png)

-> _Change http to https in pfsense web - (system – Advanced) and change port to another you don’t used.)_
![](../../attachments/Manual%20-%20Sistemas-38.png)

-> _Gpo for certificates_
![](../../attachments/Manual%20-%20Sistemas-34.png)

-> _Import certificate in ubuntu client_
-> _Settings – corticates_
-> _LDAP_
![](../../attachments/Manual%20-%20Sistemas-23.png)
![](../../attachments/Manual%20-%20Sistemas-24.png)
-> _Bind credentials you get in users and computers and go to proprieties of administrator user and attributer editor is here you get this_
-> _Create group: pfsense-admin and add the domains – like the image_
![](../../attachments/Manual%20-%20Sistemas-25.png)
-> _Add administrator in members of and members_
![](../../attachments/Manual%20-%20Sistemas-26.png)
_(just CN=Users)_

-> _Select container and select all_
-> _And in final do “;cn=pfsense-admin…” you get this like for the administrator but in pfsense-admin group_
![](../../attachments/Manual%20-%20Sistemas-27.png)
![](../../attachments/Manual%20-%20Sistemas-28.png)
## VPN SITE-TO-SITE


---
# Windows Server
## Install
![](../../attachments/Manual%20-%20Sistemas-29.png)
![](../../attachments/Manual%20-%20Sistemas-30.png)
![](../../attachments/Manual%20-%20Sistemas-31.png)
![](../../attachments/Manual%20-%20Sistemas-32.png)
![](../../attachments/Manual%20-%20Sistemas-33.png)

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