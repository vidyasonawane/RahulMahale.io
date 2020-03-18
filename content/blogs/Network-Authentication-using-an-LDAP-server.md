+++
date = "2013-12-10"
title = "Network Authentication using an LDAP server"
tags = ["LDAP"]
categories = ["technical blogs"]
+++

Hi Techies,

So far we know that, local user accounts are managed through local files (/etc/passwd) on each machine. However, it is difficult to coordinate local user accounts on many systems.

In this blog, I will look at how to set up a machine as a client, to use a network user accounts that are provided by an existing **LDAP (Lightweight Directory Access Protocol)** directory service. This allows the LDAP directory to be our central authority for all network users and groups in your organization.

User account information determines the characteristics and configuration of the account Authentication methods are used to determine if someone trying to log in should get access to the account. Network directory services can provide both user account information and authentication methods.

LDAP directory services can be used as a distributed, centralized, network user management service. Directory entries are arranged in a tree structure that can be searched. The base DN (Distinguished Name) is the base of the tree that will be searched for directory entries for users and groups.

**Key Elements for LDAP configuration**

**1. Server’s fully qualified hostname**

**2. Base DN to search for user definitions**

**3. The certificate authority (“CA”) certificate used to sign the LDAP server’s SSL certificate.**

You should ensure that the _directory-client_ yum (for _Redhat_ and _Fedora_) package group is installed, which includes the packages sssd, authoconfig-gtk, and oddjob-mkhomedir before you begin.

_System_ —> _Administration_ —> or _system-config-authentication_ can be used to modify the configuration of Identity and Authentication.

![upload](/images/upload.jpg)

Creating LDAP Account

![upload1](/images/upload2.jpg)

Downloading CA Certificate

**System-config-authentication** will automatically turn on the **sssd** service which will look up and cache LDAP user information and authentication credentials for the client. If the LDAP server is unavailable but sssd is working, the system may be able to authenticate and get information about network users from the sssd cache.

Use __getent passwd username__ to verify the account information being used. This works whether the user is a local user defined in `etc/passwd` or a network user from an LDAP service. The command will always show the definition that is actually being used by the system if there is any duplication between local users and network users. By default, the local user definition overrides the network user definition.