# vagrant

<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Vagrant.png/440px-Vagrant.png" width="200" /></p>

<ul>
  <li>
    <h4>Kubernetes Setup Using Ansible and Vagrant</h4>
    https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/
  </li>
  <li>
    <h4>Quickstart for Calico on Kubernetes</h4>
    https://docs.projectcalico.org/master/getting-started/kubernetes/quickstart
  </li>
</ul>

#### Start Vagrant VM
```shell
vagrant up node-1 --provision
```

#### Destroy Vagrant VM
```shell
vagrant destroy -f
```

#### SSH into the machine
```shell
vagrant ssh
```

#### Network
```shell
echo 1 > /proc/sys/net/ipv4/ip_forward
````

#### Run Ansible Playbook manually
```shell
ansible-playbook -i inventory.yaml playbook.yaml --flush-cache --diff -vv --limit "virtualbox"
```
