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
## Step 2: Install PostgreSQL 15 on Rocky/Alma Linux

With the PostgreSQL YUM repository in place, the next step is to update repositories. Simply run the following command to achieve this:
```
$ sudo dnf update -y
```
Next, disable the default module which, as we saw earlier, 
```
$ sudo dnf -qy module disable postgresql
```
Once the default module is disabled, proceed and install PostgreSQL 15 client and server as shown.
```
$ sudo dnf install -y postgresql15-server
```

Type 'Y' and hit ENTER every time you are prompted to import the GPG key.

You can confirm the version of PostgreSQL installed using the command:

```
$ psql -V
```
psql (PostgreSQL) 15.0

### Initialize the PostgreSQL Database
#### Change default postgre user password
```
[root@pgnode2 ~]# passwd postgres
Changing password for user postgres,
New password:
BAD PASSWORD: The password fails the dictionary check - it is too simplistic/systematic
Retype new password:
passwd: all authentication tokens updated successfully.
```
#### Following is for only Master Machine 
Before proceeding further, we need to initiliaze the initdb database which is responsible for creating a new PostgreSQL cluster. A cluster is a group or collection of several databases that are managed by a cluster.
freestar.
So, to initialize the database, run the command:
```
$ sudo /usr/pgsql-15/bin/postgresql-15-setup initdb
```

