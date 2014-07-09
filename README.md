vagrant-rails
=============

These files will help you get a Ruby on Rails environment set up on an Ubuntu virtual machine.

## Instructions

* Download Files (or clone repository if you aren't going to use it to start a new project)
* Copy `Vagrantfile.dist` to `Vagrantfile`
* Make any changes necessary to `Vagrantfile` to configure Virtual Machine
* Edit `setup.sh` to create the password for your PostgreSQL database user.
* Install VM using:
```bash
$ vagrant up
```

All shared files will be located in `/vagrant` on the VM.

__To create a new Rails app that uses PostgreSQL in the VM, change to the shared folder and execute:__

```bash
$ rails new MYAPPNAME --database=postgresql
```

## Requirements

* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant](http://www.vagrantup.com/)

## Software Installed in VM

* Ubuntu 14.04
* Ruby 2.1
* Rails 4
* Compass
* Git
* PostgreSQL 9.3
* nginx 1.6
* UFW (Uncomplicated FireWall)
* Node.js (because you just might need it for something)

_Several lines of `setup.sh` have been commented out that setup and enable the firewall. Uncomment them to close all ports except `ssh`, `http`, `https`, and `3000` (the default Rails port)_

_Disclaimer: This is an [appendTo](http://appendto.com) Labs project and as such there is no promise of support or even future development of this project. We are working on this project to meet a need at appendTo and sharing it in the spirit of open source software. If it helps you or your team meet needs as well, that is awesome – however, use at your own risk._