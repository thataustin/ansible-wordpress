ansible-wordpress
=================

[![Join the chat at https://gitter.im/thataustin/ansible-wordpress](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/thataustin/ansible-wordpress?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A set of ansible scripts the install Wordpress, wp-cli, nginx, postgresql

**Note:** Change the IPs in host.local and run with `ansible-playbook -i hosts.local site.yml`

### Deploying locally without Vagrant
If you aren't using vagrant, be sure to update `ansible_ssh_user` in `hosts.local` to match your system user

### Deploying locally with Vagrant
This setup was developed by deploying to a local [vagrant](http://www.vagrantup.com/) environment running Ubuntu
If you're looking to deploy locally like that, remember to do the following:

1. `ssh-add ~/.vagrant/insecure_private_key`
2. Modify hosts.local to include your local VM's IP

### Protips with Vagrant

If you just want a vanilla wordpress install to test out locally, run the following:

    vagrant plugin install vagrant-hostmanager
    vagrant up
    vagrant provision # don't need this part if it's never been provisioned

That will create an Ubuntu VM and install wordpress, postgress and the wordpress-cli tools on it.

The default Vagrantfile is configured with host-only networking options, meaning you can only reach it from on your host machine.  You can reach it at the following addresses:

    wordpress.dev
    192.168.42.100

The hostmanager plugin adds a line to your host machine's `/etc/hosts` file to facilitate alias.

If you'd like to be able to reach the site from outside of your VM, you can configure the box with [bridged networking options](https://docs.vagrantup.com/v2/networking/public_network.html).  Follow the Vagrant docs to do so.


You can ssh to the vagrant machine by running the `vagrant ssh` command, and you can find the wordpress site installed in this director:

    /srv/wordpress

If you have any other questions, feel free to get ahold of me.
