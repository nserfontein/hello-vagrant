# Basic Vagrant
### Traditional Way
- Lots of manual steps
- Have to install and configure needed apps and libraries

### Vagrant Way
#### Run preconfigured box
```bash
cd vms/ubuntu16
vagrant init bento/ubuntu-16.04
vagrant up --provider virtualbox
vagrant ssh
```

# The Vagrant file
### Use one of the official boxes
- https://app.vagrantup.com/boxes/search
```bash
vagrant init bento/ubuntu-16.04
# this will pull down the box and cache it for next time
vagrant up --provider virtualbox
```

### Add your own box
```bash
vagrant box add http://somewhere.com/myvagrant.box
```

# Communicating with Vagrant Box









