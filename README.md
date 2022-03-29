# SEPE AWX EE

A Custom Ansible Execution Environment for Platform Engineering. 

How to build locally:

```bash
pip install -r build-reqs.txt                       # or however you deal with python
podman pull quay.io/ansible/ansible-runner:latest   # or docker
podman pull quay.io/ansible/ansible-builder:latest  # or docker
ansible-builder build -v3 --tag awx-ee:local
```
