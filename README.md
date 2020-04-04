# PackagingRepo
 
This repository contains sources for building the vsftpd.rpm package. Please, follow the instructions below to get started.
 
## Install required packages

Run the commands below to install packages required for building rpm packages

```bash
$ yum -y update
$ yum install rpm-build rpmdevtools
```

## Create build directory structure

To setup the build environment on Centos7 go to users home directory and run the command below

```bash
$ rpmdev-setuptree
```

Make sure the directory was created succesfully

```bash
$ ls -l rpmbuild

drwxr-xr-x 2 root root 6 Oct 25 03:09 BUILD
drwxr-xr-x 2 root root 6 Oct 25 03:09 RPMS
drwxr-xr-x 2 root root 6 Oct 25 03:09 SOURCES
drwxr-xr-x 2 root root 6 Oct 25 03:09 SPECS
drwxr-xr-x 2 root root 6 Oct 25 03:09 SRPMS
```

If the directory structure failed to create by the command above, you can manually create it

```bash
$ mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS,tmp}
```

## Install git

Skip this step if you already have git set up on your Centos7 build environment

```bash
$ yum install git
```

## Clone current git repo

Click on the “Clone or download” button and copy the url of the repo. Run the command below to clone current remote repository to your local machine

```bash
$ git clone repo_url
```
## Copy source files to the build directory

Copy the tarball from the local git directory the ~/rpmbuild/SOURCES directory 

```bash
$ cp vsftpd-3.0.2.tar.gz ~/rpmbuild/SOURCES
```

Copy the .spec file to the ~/rpmbuild/SPECS directory

```bash
$ cp vsftpd.spec ~/rpmbuild/SPECS
```
## Install package dependancies

Install vsftpd package dependencies 

```bash
$ yum install -y pam-devel libcap-devel openssl-devel tcp_wrappers-devel
```

## Build your RPM

Build your rpm by executing following commands

```bash
$ cd ~/rpmbuild
$ rpmbuild -ba SPECS/vsftpd.spec
```