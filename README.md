## Description

The purpose of the project is to install a very basic http server (compiled from a basic GO scipt) reachable through nginx as load balancer. It will install 3 nodes :

* 1 node where with Nginx is installed that will work as a load balancer
* 2 application nodes 

The purpose is to receive the following message from the load balancer that hosts the very-basic-http-server :

    Hi there, I'm served from 192.168.2.10!

## Requirements

* Git
 - Debian/Ubuntu : sudo apt-get install git
 - Fedora, Red Hat or CentOS : sudo yum install git
 - SUSE : sudo zypper -v install git
 - Windows : gitbash or cygwin

* [VirtualBox](https://www.virtualbox.org). The CentOS 7 vagrant box is [downloadable here](https://github.com/tommy-muehle/puppet-vagrant-boxes/releases/download/1.1.0/centos-7.0-x86_64.box)

* [Vagrant](https://www.vagrantup.com/downloads.html). It works with a lot of Linux platform like Fedora/Centos/RHEL/Debian/Ubuntu and also with Windows or MaxOSX.

## Usage :  How To Build The Virtual Machine

After installing the required applications, download the vagrant box :

    host $ vagrant box add centos7_vbadd_puppet "https://github.com/tommy-muehle/puppet-vagrant-boxes/releases/download/1.1.0/centos-7.0-x86_64.box"
 and what remains is to build the VMs :

    host $ git clone https://github.com/4LeXFiDin/sainsburys_project.git
    host $ cd sainsburys_project
    host $ vagrant up --provision

### Testing

You can either connect to the web server with the URL with you browser :
 - http://192.168.2.10
    
or type the following commande from a terminal :
 - curl http://192.168.2.10
   
You can test the 2 applications behind the load balancer with the following URLs :
 - http://192.168.2.11:8484
 - http://192.168.2.12:8484

## Continuous Integration

 - [TravisCI/4LeXFiDin](https://travis-ci.org/4LeXFiDin/vagrant_nginx_round-robin/builds)

## Provisionning

- Chef Solo

### Cookbooks

 - build-essential
 - nginx
 - ohai
 - yum
 - yum-epel

## License and Author

Author:: Alexandre D.

Copyright:: No :)
