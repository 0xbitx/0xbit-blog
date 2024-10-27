
<h1 align="center"> mikrotik-sec </h1>

<h3 align="center"> MikroTik Router Security Guide </h3>

## Introduction

This guide provides a full set of scripts and configurations for securing your MikroTik router against various types of attacks, including DDoS, brute force, unauthorized access, and more. By following these steps, you'll ensure that your router is well-protected against common security threats.

---

## Pre-Requisites

- **RouterOS Version**: MikroTik RouterOS v6 or higher.
- **Access**: Winbox, WebFig, or SSH access to your router.
- **Backup**: Backup your current configuration before applying these scripts.

## Backup Configuration

Before applying any security settings, backup your router’s current configuration:
```shell
/system backup save name=pre_security_backup
/export file=pre_security_config
```
Scripts and Configurations
1. Secure Firewall Rules

This firewall script protects your router by blocking unwanted traffic, limiting login attempts, and preventing DDoS attacks.

```rsc
/ip firewall filter
add chain=input protocol=tcp dst-port=21,22,23,80,8291 action=drop comment="Drop unneeded ports"
add chain=input connection-state=invalid action=drop comment="Drop invalid connections"
add chain=input connection-state=established,related action=accept comment="Allow established connections"
add chain=input protocol=tcp dst-port=22,8291 src-address-list=allowed_admins action=accept comment="Allow admin access"
add chain=input protocol=tcp src-address-list=blacklist action=drop comment="Drop blacklisted IPs"
add chain=input protocol=icmp action=accept comment="Allow ICMP (Ping)"
add chain=input action=drop comment="Drop all other traffic"
```
  Allow only specific ports: Drops traffic to non-essential ports.
  Admin Access Control: Allow access only to specified admin IPs (allowed_admins list).
  Blacklist: Drops any traffic from blacklisted IPs.
  Drop all else: Drops all other connections as a final rule.

2. Access Control and Remote Management Restrictions

Restrict access to the router’s management interfaces.

```rsc

/ip service
set telnet disabled=yes
set ftp disabled=yes
set www disabled=yes
set ssh address=192.168.1.0/24 disabled=no port=2200
set winbox address=192.168.1.0/24 port=8291
set www-ssl disabled=yes
```
  Disable unused services: Disables Telnet, FTP, and Web access for increased security.
  Limit SSH and Winbox: Restricts access to SSH and Winbox from a specified internal subnet.

3. Brute Force Protection

This script limits login attempts by dynamically blacklisting IP addresses after several failed attempts.

```rsc
/ip firewall address-list
add list=blacklist timeout=1d comment="Temporary blacklist for brute force prevention"
/ip firewall filter
add chain=input protocol=tcp dst-port=22,8291 connection-state=new src-address-list=blacklist action=drop comment="Drop brute force IPs"
add chain=input protocol=tcp dst-port=22,8291 connection-state=new action=add-src-to-address-list address-list=blacklist address-list-timeout=1h comment="Add failed login IPs to blacklist"
```
4. VPN Configuration for Secure Remote Access

Secure remote management access by using a VPN with L2TP/IPsec.

```rsc

# Set up L2TP with IPsec
/interface l2tp-server server set enabled=yes default-profile=default use-ipsec=yes ipsec-secret=your_secret_key
/ppp profile set default local-address=192.168.10.1 dns-server=192.168.10.1
/ppp secret add name="vpn_user" password="secure_password" service=l2tp profile=default
```
  L2TP/IPsec Setup: Configures the router for VPN access, securing remote management.
  User Authentication: Sets up a dedicated VPN user.

5. DNS Security

Securing DNS prevents cache poisoning and DNS spoofing attacks.

```rsc

/ip dns
set allow-remote-requests=no servers=8.8.8.8,1.1.1.1
/ip firewall filter
add chain=input protocol=udp dst-port=53 action=drop comment="Drop external DNS requests"
```
  Local DNS only: Ensures DNS requests are handled only for internal clients.
  External DNS requests: Drops DNS requests from outside the router.

6. Logging and Monitoring

Enable logging to monitor potential security issues.

```rsc

/system logging
add topics=firewall action=memory
add topics=info,warning,error action=disk
```
  Firewall Logs: Logs all firewall activity for review.
  System Logs: Logs errors, warnings, and general information to the disk.

7. Scheduling Scripts

You can schedule some scripts to run periodically, like updating blacklists or performing security checks.

```rsc

/system scheduler
add name="update_blacklist" interval=1d on-event="/ip firewall address-list remove [find list=blacklist]"
```
This schedule clears the blacklist every 24 hours.

8. block access to Starlink page from a particular port (like port 2) 
Define IP addresses or DNS names for Starlink's domains (update as needed)
```rsc
/ip firewall layer7-protocol add name=block_starlink regexp="^.*starlink.*\$"
/ip firewall filter add chain=forward src-port=2 protocol=tcp layer7-protocol=block_starlink action=drop comment="Block Starlink access from port 2"
```

Layer7 Protocol: This uses regular expressions to match Starlink-related DNS names.
Filter Rule: Blocks traffic from devices connected to port 2 when attempting to access Starlink.
This rule will need to be updated if IPs or domains change, or additional specific domains are necessary for broader blocking.
