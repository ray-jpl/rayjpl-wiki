---
title: "Directory Information Tree"
enableToc: true
tags:
- LDAP
- DIT
---

LDAP directories are organized in a hierarchical tree structure, similar to the directory structure of a file system. This structure is also known as the Directory Information Tree (DIT). At the top of the tree is the root node, and below that are branches and sub-branches that represent the various objects and attributes in the directory.

Each object in the directory is represented by an entry in the tree, and each entry is identified by a unique name called a distinguished name (DN). The distinguished name of an entry is composed of the names of all the nodes (or branches) that lead to that entry, starting from the root of the tree.

For example, suppose we have an LDAP directory that contains information about employees in a company. The top-level node in the tree might be the organization's name, followed by sub-nodes for departments, teams, and individual employees. The distinguished name for an employee named "John Smith" in the "Sales" department might look something like this:

cn=John Smith,ou=Sales,ou=Departments,o=MyCompany,c=US

Here, "cn" stands for "common name", "ou" stands for "organizational unit", "o" stands for "organization", and "c" stands for "country". These are all examples of attributes that can be used to identify and categorize entries in the directory. LDAP DNs also ascend the tree from left to right, Here the John Smith is directly under Sales and Sales is part of Departments and so on.

It is common practice to refer to the leftmost component of an entry's DN as the RDN for that entry. In the above example, the RDN would be cn=John Smith.

The distinguished name of an entry is important because it provides a unique identifier that can be used to retrieve or modify the entry. When a client application wants to access an entry in the directory, it sends a request to the LDAP server that includes the distinguished name of the entry it wants to access.



## References
- https://ldap.com/ldap-dns-and-rdns/