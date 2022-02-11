# Devops Challenge

The Goal of this Challenge is to Learn how Terraform, Kubernetes and Fluxcd can play together to build a full infrastructure as code setup with automatic CI/CD deployment.

Challenge:
Create the needed Terraform and Kubernetes git repositories that allows you to tear up fully working kubernetes cluster with just editing a file and running 1-2 commands. The cluster should run [Fluxcd](https://fluxcd.io/) to apply yaml files from a github repository.

What should be configurable:
- CIDRS for pod and service networks

The cluster should run at least one custom deployment, e.g. a Hello World or Echo container.
Any checking to the repositories with the K8s yaml files should be automatically applied by flux using kustomize. 

Deliverable:

- 2 Github Repositories:
    - terraform + initial shell scripts, everything needed to get the cluster up and running.
    - Cluster states: organization of yaml files that are applied by flux+kustomize
- Readme and explanation of design decision, prerequisites and step by step instruction to get everything running.

Evaluation Criterias:
- number of commands and files to edit to make this run should be minimal
- documentation
- explanation of decisions
- organization of the code.

Options/hints:
The target Platform to run the nodes on should either be libvirtd or AWS. For a free setup just install any linux machine or VM and install+run libvirtd. 

Bonus Points:
- ingress nginx works
- calico for networking
- ipv6
- flux deployment automation  that automatically updates minor releases of a hello world app

tipps:
if you use libvirt you can also run it easily on a remote linux machine:

`provider "libvirt" {
uri = "qemu+ssh://root@192.168.111.61/system?keyfile=~/yannick/.ssh/qb01ecdsa"
}`

 if you use k3s ontop of [k3os](https://github.com/rancher/k3os) as a distribution you can simply run a quick and dirty webserver with `python3 -m http.server 8003`  to serve the config yaml