# Ansible Playbook

Ansible playbook for base and initial configuration of web server hosting my personal websites.  After successful execution of this playbook, however, there is still some manual work to import databases, copy site content, etc.

## Assumptions
Before you can run this, a few things are assumed:

- You have a clean, minimal Ubuntu 14.04 host up and running
- You have a user account with password-less SSH access to the machine
- You have sudo privileges on the remote host
- You have created a `hosts` file with something like:

```ini
[web]
web01
```

## Use
Once you've satisfied the the above assumptions, you can execute:

    ansible-playbook web.yml -i hosts -K

### Testing in a VM (KVM)
A simple way to test locally in a virtual machine using libvirt + KVM:

```console
sudo virt-install -n web01 -r 1024 --vcpus 2 -l http://ubuntu.mirror.ac.ke/ubuntu/dists/trusty/main/installer-amd64/ --os-type=linux --os-variant=ubuntusaucy --disk /home/aorth/software/vms/web01.qcow2,device=disk,bus=virtio,format=qcow2,size=40 --vnc --cpuset=1,2 -x "auto=true priority=critical url=http://blah.com/~aorth/preseed/public/ubuntu-14.04.cfg"
```

This boots from a network Ubuntu mirror, then uses a preseed to automate the OS installation.

### Testing in Vagrant
Not as simple as on GNU/Linux with KVM, but still easy:

```console
vagrant init ubuntu/trusty64
```

Then uncomment the following line in your `Vagrantfile`:

```ruby
# Create a public network, which generally matched to bridged network.
# Bridged networks make the machine appear as another physical device on
# your network.
config.vm.network "public_network"
```

And finally, bring the machine up:

```console
vagrant up
```
