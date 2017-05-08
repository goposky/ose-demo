## Openshift v3 demo

***To be updated shortly.***

This is a demo openshift v3 environment consisting of 1 master, 1 node, and a registry host.
The VagrantFile was tested and working on MacOS Sierra and Fedora 22.

### Prerequisites
Virtualbox, vagrant and ansible should be installed on the host machine.
Atleast 8GB RAM recommended for the host machine.
Red Hat provides a free 1 month evaluation subscription of Openshift container platform. The subscription can be obtained here: https://access.redhat.com/products/red-hat-openshift-container-platform/evaluation

### Setup
```bash
git clone git@github.com:goposky/ose-demo
cd ose-demo
vagrant up
open https://10.1.2.15:8443
```
