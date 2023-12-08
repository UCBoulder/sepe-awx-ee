# SEPE AWX EE

A Custom Ansible Execution Environment for Platform Engineering using
python 3.9.

Originally cloned from the [Ansible awx-ee repository](https://github.com/ansible/awx-ee).

### How to build locally:

```bash
pip install -r build-reqs.txt                       # or however you deal with python
podman pull quay.io/ansible/ansible-runner:latest   # or docker
podman pull quay.io/ansible/ansible-builder:latest  # or docker
ansible-builder build -v3 -t awx-ee:local
```

This should result in a podman image, for example:

```
$ podman images
REPOSITORY                       TAG         IMAGE ID      CREATED       SIZE
localhost/awx-ee                 local       f6c5989cd851  3 hours ago   1.99 GB
```

To run the local execution environment image above in a container with a
bash prompt:

```
$ podman run -it f6c5989cd851 /bin/bash
bash-5.1# python3 -V
Python 3.9.19
bash-5.1# exit
```

### Automated Builds

See the `.github` directory for more information, but essentially, commits to the `devel` branch will cause a new version of this container to be built and hosted at:

```
ghcr.io/ucboulder/sepe-awx-ee/awx-ee:latest
```

### Dependabot

Dependabot is configured to automatically version-bump our python
dependencies and will automatically generate pull requests.
Unfortunately, at this time it does not support either Ansible Galaxy or
"bindep" dependencies. See `.github/dependabot.yml` for additional
details.

Approving dependabot-generated PRs and merging to the `devel` branch
should automatically result in an updated package once the deploy
workflow (see `.github/workflows/deploy.yml`) completes.

> **Note**: Dependabot is currently configured to ignore major version
> updates for **ansible**.
