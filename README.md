# ansible-vagrant

## description

ansible roles development environment using vagrant

## dependencies

1. `virtualbox (latest)`
2. `vagrant (latest)`
3. `ansible (latest)`

## vagrant configuration variables explained

```
memory: 2048                  # ram for each vm
cpus: 1                       # cpus for each vm

nodes: 2                      # number of vms
box: centos/7                 # vagrant box for each vm
playbook: playbook.yml        # playbook used to run role(s)
```
**Note:** vagrant automatically assigns VM hostnames and private IPs like this:
```
node1 - 192.168.77.21
node2 - 192.168.77.22
...
```

## usage

1. create role and put it in `roles/` directory.
2. create custom playbook (e.g. `playbook.yml`) to test your role.
3. change `config.yml` variables for your needs.
4. run command `vagrant up` and wait for provisioning.

**Note:** do not try to change anything in `Vagrantfile`
