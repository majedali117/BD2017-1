### CM/CDH Installation commands
Download CM 5.8.3 repo file as following:
```
wget https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/cloudera-manager.repo
```
Edit the downloaded repo file and edit the ```baseurl``` as follows:
```
[achintya@kumarnode0 ~]$ sudo nano cloudera-manager.repo

[cloudera-manager]
# Packages for Cloudera Manager, Version 5, on RedHat or CentOS 6 x86_64        
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.8.3/
gpgkey =https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/RPM-GPG-KEY-cloudera
gpgcheck = 1


```
Finally, copy this edited file to ```/etc/yum.repos.d/```
```
cp cloudera-manager.repo /etc/yum.repos.d/ 
```


The above can be also achieved by downloading an installer as shown below:
Download CM 5.8.3 installer as following:
```
[achintya@kumarnode0 ~]$ wget http://archive.cloudera.com/cm5/installer/5.8.3/cloudera-manager-installer.bin
```
Set password for all users (in my case, user ```achintya```) on all nodes:
```
[achintya@kumarnode0 ~]$ passwd
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
```
Enable password login for CM on all nodes:
```
[achintya@kumarnode0 ~]$ sudo perl -p -i -e "s/^PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config
[achintya@kumarnode0 ~]$ sudo service sshd restart
```
