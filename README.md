ansible-wordpress
=================

Wordpress, wp-cli, nginx, postgresql

**Note:** Change the IPs in host.local and run with `ansible-playbook -i hosts.local site.yml`

### Deploying locally without Vagrant
If you aren't using vagrant, be sure to update `ansible_ssh_user` in `hosts.local` to have to match your system user

### Deploying locally with Vagrant
This setup was developed by deploying to a local [vagrant](http://www.vagrantup.com/) environment running Ubuntu
If you're looking to deploy locally like that, remember to do the following:

1. `ssh-add ~/.vagrant/insecure_private_key`
2. Modify hosts.local to include your local VM's IP
