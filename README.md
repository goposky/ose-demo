## Openshift v3 demo

This is a demo openshift v3 environment consisting of 1 master, 1 node, and a registry host.
The VagrantFile was tested and working on MacOS Sierra and Fedora 22.

### Host pre-requisites
Software requirements: virtualbox, vagrant, ansible

Hardware requirements: 

### Setup
```bash
git clone git@github.com:goposky/ose-demo
cd ose-demo
vagrant up
open https://10.1.2.15:8443
```
