##GlusterFS Setup for Kubernetes
This repo has Kubernetes yaml files for creating a GlusterFS service|endpoints and Persistent Volumes.

##Limit Access to Gluster volumes

```shell
for x in {0..9}; do gluster volume set vol$x auth.allow 104.236.156.39,104.236.142.45,104.236.145.36; done
```
