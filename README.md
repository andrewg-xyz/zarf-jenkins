# Jenkins Zarf Package

Jenkins Zarf package example. 

## Quickstart
* prerequisite: install zarf on your machine, have a k8s cluster up and running

```
# follow a few onscreen prompts when running zarf commands
zarf package create
zarf init
zarf package deploy
```

> Running `scripts/get_login.sh` prints login information for the zarf jenkins package.

---
## Explanation
### zarf.yaml - package definition

The `zarf.yaml` file has two components.

1. `prepare-jenkins` - this component applies a few kubernetes manifests to create a jenkins volume and service account

2. `jenkins` - this component defines the source helm chart and images required.

### zarf package create

Running `zarf package create` will use the `zarf.yaml` definition and will create a *.tar.zst file as a declarative artifact. This artifact, the zarf binary, and init package are all that is required to install onto a kubernetes cluster

### zarf init

Running `zarf init` installs zarf into the cluster. It includes an embedded image registry (optional) and the zarf agent (or worker bee). Zarf init also has logging or git-server optional components

### zarf package deploy

Running `zarf package deploy` installs the jenkins package into the cluster.
