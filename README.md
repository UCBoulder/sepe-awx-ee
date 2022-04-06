# SEPE AWX EE

A Custom Ansible Execution Environment for Platform Engineering. 

### How to build locally:

```bash
pip install -r build-reqs.txt                       # or however you deal with python
podman pull quay.io/ansible/ansible-runner:latest   # or docker
podman pull quay.io/ansible/ansible-builder:latest  # or docker
ansible-builder build -v3 --tag awx-ee:local
```

### Automated Builds

See the `.github` directory for more information, but essentially, commits to the `devel` branch will cause a new version of this container to be built and hosted at:

```
ghcr.io/ucboulder/sepe-awx-ee/awx-ee:latest
```

Additionally, dependabot is configured to automatically version-bump our python dependencies. Unfortunately, at this time it does not support either Ansible Galaxy or "bindep" dependencies.
