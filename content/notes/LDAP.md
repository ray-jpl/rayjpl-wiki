---
title: "LDAP"
enableToc: true
tags:
- LDAP
---

Lightweight Directory Access Protocol (LDAP) is a vendor-neutral protocol used for accessing and maintaining distributed directory information services. A directory service is like a database that stores information about network resources, such as users, computers, printers, and other devices.

LDAP is commonly used to provide authentication and authorization services for networked resources. For example, when you log in to a computer that's part of a domain, the computer might use LDAP to check your username and password against the directory service to determine whether you're authorized to access the network.

LDAP is a client-server protocol, which means that there's a client application that sends requests to a server application to access the directory information. The client and server communicate using TCP/IP, and LDAP requests and responses are usually transmitted over port 389 or 636 (if using SSL).

LDAP directories are organized into a hierarchical tree structure, called [[notes/Directory Information Tree (DIT)]], where each node in the tree represents an object, such as a user or a group. Each object is identified by a unique name called a distinguished name (DN), which consists of a series of attributes separated by commas. For example, the DN for a user might be "cn=John Doe, ou=Users, dc=example, dc=com".




LDAP uses a query language called LDAP Query Language (LDAPQL) to search and retrieve information from the directory. LDAP queries are similar to SQL queries, but they use a different syntax and support different search filters and operations.

## References
- https://www.onelogin.com/learn/what-is-ldap