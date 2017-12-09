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
#### Status
```bash
vagrant status
```

#### SSH
```bash
vagrant ssh
```

#### Shared folders
##### Preconfigured share
```bash
vagrant ssh
cd /vagrant
```

##### Custom share
- Use case: source code
- High performance penalty
- Edit Vagrantfile:
```yaml
config.vm.synched_folder ".", "/vagrant", disabled: true
config.vm.synched_folder "host-path", "/guest-path"
```

#### Reload Vagrantfile
- After making changes
```bash
vagrant reload
``` 






