# Basic Vagrant
### Traditional Way
- Lots of manual steps
- Have to install and configure needed apps and libraries

### Vagrant Way
#### Run preconfigured box
- See sections below for more details
```bash
vagrant init bento/ubuntu-16.04
vagrant up --provider virtualbox
vagrant ssh
```

# The Vagrant file
### Use one of the official boxes
- https://app.vagrantup.com/boxes/search
```bash
cd boxes/ubuntu16
vagrant init bento/ubuntu-16.04
# this will pull down the box and cache it for next time
vagrant up --provider virtualbox
```

### Add your own box
```bash
vagrant box add http://www.mywebsite.com/myvagrant.box
```

# Communicating with Vagrant Box
### Status
```bash
vagrant status
```

### Change running state
```bash
vagrant suspend
vagrant resume
# graceful shutdown
vagrant halt
# forceful shutdown
vagrant halt --force
# remove VM (but not shared folders)
vagrant destroy
```

### SSH
```bash
vagrant ssh
```

### Reload Vagrantfile
- After making changes
```bash
vagrant reload
``` 

### Shared folders
#### Preconfigured share
```bash
# on guest
cd /vagrant
```

#### Custom share
- Use case: source code
- High performance penalty
- Edit Vagrantfile:
```ruby
# disable preconfigured share
config.vm.synched_folder ".", "/vagrant", disabled: true
# create custom share
config.vm.synched_folder "host-path", "/guest-path"
```

# Network Access
### Port Forwarding
- Edit Vagrantfile
```ruby
config.vm.network "forwarded_port", host: 8080, guest: 80
```




