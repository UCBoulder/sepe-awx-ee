# SEPE AWX EE

A Custom Ansible Execution Environment for Platform Engineering. 

Before creating a PR, run one of the following commands locally. This will
accomplish 2 things:

1. Update the build context (Basically apply any upstream updates to Containerfile)
2. Ensure that the build succeeds.

## Regenerating the build context with podman:

```bash
$ tox -epodman
```

## Regenerating the build context with docker:

```bash
$ tox -edocker
```