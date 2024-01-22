# PostgreSQL Replication Setup
Linux Version: Rocky Linux 9

|Machine IPS| 
|----| 
|192.168.10.190| 
|192.168.10.191| 
|192.168.10.192| 

Postgre installation will take place in 192.168.10.190 machine

## Step 1: Add the PostgreSQL Repository
The default version of PostgreSQL on Appstream repositories is PostgreSQL 10.
```
$ sudo dnf module list postgresql
```

To install the latest PostgreSQL version, we need to, first, install the PostgreSQL YUM repository on our system as shown.

--------------- Rocky & AlmaLinux 9 --------------- 
```
$ sudo dnf install https://download.postgresql.org/pub/repos/yum/reporpms/EL-9-x86_64/pgdg-redhat-repo-latest.noarch.rpm
```
