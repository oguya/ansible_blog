Playbook for base and initial configuration of web server hosting my personal websites.

### To use
Create a new Ubuntu 14.04 host, add a user account, copy your SSH public key, then execute:

    ansible-playbook site.yml -i hosts --limit=web01 -K

### Testing
For testing, use a VM, ie with KVM and libvirt:

```console
virt-install -n web01 -r 1024 --vcpus 2 -l http://ubuntu.mirror.ac.ke/ubuntu/dists/trusty/main/installer-amd64/ --os-type=linux --os-variant=ubuntusaucy --disk /home/aorth/software/vms/web01.qcow2,device=disk,bus=virtio,format=qcow2,size=40 --vnc --cpuset=1,2 -x "auto=true priority=critical url=http://blah.com/~aorth/preseed/public/ubuntu-14.04.cfg"
```
