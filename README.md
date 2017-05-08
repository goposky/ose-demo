## Openshift v3 demo

**Incomplete. To be updated shortly.**

This is a demo openshift v3 environment consisting of 1 master, 1 node, and a registry host.
The VagrantFile was tested and working on MacOS Sierra and Fedora 22.

### Host machine pre-requisites
Virtualbox, vagrant and ansible.
Atleast 8GB RAM recommended.

### Setup
```bash
git clone git@github.com:goposky/ose-demo
cd ose-demo
vagrant up
open https://10.1.2.15:8443
```
