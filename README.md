##GlusterFS Setup for Kubernetes
This repo has Kubernetes yaml files for creating a GlusterFS service|endpoints and Persistent Volumes.

##Limit Access to Gluster volumes

```shell
for x in {0..9}; do gluster volume set vol$x auth.allow 104.236.156.39,104.236.142.45,104.236.145.36; done
```

## Setup Gluster

```shell
# Install glusterfs-server on all nodes
apt-get install glusterfs-server
apt-get install glusterfs-client

# Probe the peer nodes from node k1
gluster peer probe k2
gluster peer probe k3

# Create the directory for the gluster volumes
mkdir /mnt/gluster

# Create volumes
gluster volume create vol0 replica 2 transport tcp k2:/mnt/gluster k3:/mnt/gluster force

# Start the new volumes
gluster volume start vol0

# Test mounting the gluster volume
sudo mount -t glusterfs k1:/vol1 /tmp/vol1
```


