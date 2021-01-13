## Requirements
> Vagrant

> Oracle VM VirtualBox


## Vagrant
From [trusty](trusty) folder, run the following command to create a virtual machine.
```shell
$ vagrant up
```

In order to connect via ssh all you got do is just run:
```shell
$ vagrant ssh
```
If the above command doesn't work, you have another way to achieve that. Generate the ssh config file by running:
```shell
$ vagrant ssh-config > ssh_config
```
Then, just run a ssh command:
```shell
$ ssh -F ssh_config wordpress
```

If you are using Virtual Box, install the following plugin:
```shell
$ vagrant plugin install vagrant-vbguest
```
Installing this plugin Virtual Box will be able to share the `/vagrant` folder.


### AWS
Install AWS Plugin:
```
$ vagrant plugin install vagrant-aws
```
Install Dummy Box:
```
$ vagrant box add --force dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```

```
$ vagrant up aws_web --provider=aws
```


## Ansible
Execute a remote command on a machine:
```shell
$ ansible wordpress -u vagrant -i hosts --private-key .vagrant/machines/wordpress/virtualbox/private_key -m shell -a 'echo Hello, World'
```

### Playbook

```shell
$ ansible-playbook provisioning.yml -u vagrant -i hosts --private-key .vagrant/machines/wordpress/virtualbox/private_key
```


## Details
I've had some issues with `vagrant ssh`. In order to fix it, I had to install the specifics versions:

* Vagrant 2.1.5
* Ansible 2.9.16
* VirtualBox 5.2.44

If you face some problems when connecting to a VM after destroying it and creating another one, just append the following line to your user profile:
```
$ echo "export ANSIBLE_HOST_KEY_CHECKING=False" >> ~/.bashrc
```