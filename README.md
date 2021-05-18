# Ansible Anwendertreffen Demo Playbooks

This repository contains the playbooks used in the Live Demo from my presentation at the second "Ansible Anwendertreffen" conference.  
The `k3s-install.yml` playbook and the roles `k3s-agent`, `k3s-server` and `k3s-bootstrap` are taken from another repository: https://github.com/TimGrt/kubernetes-installation  
The `kubernetes-dashboard.yml` playbook and the role `kubernetes-dashboard` was build especially for the Live Demo.  
Both playbooks were used to demonstrate the usage of execution environments.  
The playbooks are intended to install a Kubernetes cluster on a Raspberry Pi cluster, the cluster nodes were prepared before with the playbook from this repository: https://github.com/TimGrt/prepare-rpi-hosts

![CodeFactor Grade](https://img.shields.io/codefactor/grade/github/timgrt/ansible-anwendertreffen-demo-playbooks/main)

## Requirements

Running the playbook requires ansible-base (if not run with the execution environment as in the Live Demo).
```bash
pip3 install ansible-base
```

The following Ansible collections are necessary:
* community.general
* ansible.posix
* community.kubernetes
* ansible.netcommon

Installing the collections can be done with the _requirements.yml_.
```bash
ansible-galaxy collection install -r requirements.yml
```

The following Python packages are necessary:
* netaddr
* openshift

Install the python packages.
```bash
pip3 install netaddr openshift
```

## Execution

The playbooks can be run with the execution environment from this repository: https://github.com/TimGrt/ansible-anwendertreffen-demo-execution-environment  
Run the playbooks with Ansible directly in this order:

1. Kubernetes cluster installation
```bash
ansible-playbook -i hosts k3s-install.yml
```
2. Kubernetes Dashboard deployment
```bash
ansible-playbook -i hosts kubernetes-dashboard.yml
```

## Author

Created 2021 by Tim Grützmacher