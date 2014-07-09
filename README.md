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

__To create a new Rails app that uses PostgreSQL in the VM, change to the shared folder (defaults to `/vagrant/`) and execute:__

```bash
$ vagrant ssh
$ cd /vagrant
$ rails new MYAPPNAME --database=postgresql
```

Then on your local machine, edit `config/database.yml` and supply the following information for `default`:

```yaml
default: &default
  adapter: postgresql
  encoding: unicode
  host: localhost
  port: 5432
  pool: 5
  username: rails_user
  password: {{PASSWORD_FROM_SETUP_SH}}
```

Then create the database with:

```bash
$ rake db:create db:migrate
```

To run the site:

```bash
$ cd MYAPPNAME
$ rails server
```

Once you do this, you can access your application here: <http://192.168.33.10:3000> (Unless you changed the IP settings in the Vagrantfile).

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

## Additional Information

### Sublime Text Users

If you are experiencing problems with files not syncing correctly to your VM while using NFS sharing, add this to the root object in your `*.sublime-project` files:

```js
"settings": {
    "atomic_save": false
}
```

---

_Disclaimer: This is an [appendTo](http://appendto.com) Labs project and as such there is no promise of support or even future development of this project. We are working on this project to meet a need at appendTo and sharing it in the spirit of open source software. If it helps you or your team meet needs as well, that is awesome – however, use at your own risk._