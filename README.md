# alibabarke
## we will install RKE with Three HA node as work controlplane, etcd and worker by simple Ansible Playbook

### 1. Update Operating System
```
apt update -y;apt upgrade -y
```

### 2. Create your ansible inventory file

### 3. Add hosts of RKE to your /etc/hosts such as follow
```
172.18.28.130	rke-master-01
172.18.28.131	rke-master-02
172.18.28.132	rke-master-03
```

### 4. Create RKE user with following command
```
ansible-playbook -i inventory 01-create-rke-user.yaml
```

### 5. Enable Requiered Kernel Modules with following playbook
```
ansible-playbook -i inventory 02-required-kernel-modules.yml
```

### 6. Disable SWAP on all of nodes
```
ansible-playbook -i inventory 03-disable-swap-modify-sysctl.yaml
```

### 7. Create your RKE cluster with following command and setup your cluster with interactive mode
```
rke config
```

### 8. Up your cluster
```
rke up
```

### 9. export your cluster to your bash sh or zsh
```
export KUBECONFIG=/home/mrtshoot/alibaba/rke/kube_config_cluster.yml
```
