# openstack-exporter ROCK

This is a ROCK OCI image for openstack-exporter.

More information is coming.

For now, if you want to play with it:

```bash
> sudo snap install rockcraft --edge --classic
> rockcraft pack
```

Now that you have created the ROCK, you can import it into
your local docker repository. Using skopeo is a good idea as
it will help ensure that all layers of the image are imported
into docker (this is just the top layer).

```bash
> skopeo --insecure-policy copy oci-archive:openstack-exporter_1.7.0_amd64.rock docker-daemon:openstack-exporter:1.7.0
```

If you are interested in giving it a go in Microk8s, you can
export the image from your docker registry and then into the
microk8s registry:

```bash
> docker save openstack-exporter:1.7.0 > ./openstack-exporter_1.7.0.tar
> microk8s ctr image import ./openstack-exporter_1.7.0.tar
# Try with sunbeam
> juju attach-resource openstack-exporter openstack-exporter-image=openstack-exporter:1.7.0
```
