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
Then, justa run a ssh command:
```shell
$ ssh -F ssh_config wordpress
```


## Ansible
Execute a remote command on a machine:
```shell
$ ansible wordpress -u vagrant --private-key /path/to/private_key -i hosts -m shell -a 'echo Hello, World'
```
