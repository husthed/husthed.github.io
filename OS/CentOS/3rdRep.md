There are three repositories used: EPEL, Remi, RPMFusion. 

## EPEL repository
### What is EPEL
EPEL is the abbriviation of Extra Packages for Enterprise Linux.
### Install
````
$ sudo yum install epel-release
````

## Remi repository
### Install
````
$ sudo yum install http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
$ sudo sed -i 's/enabled=0/enabled=1/g' /etc/yum.repos.d/remi.repo
````

## RPMFusion repository
### Install
````
sudo yum install http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el7.rf.x86_64.rpm
````
