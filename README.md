# weave-kube
Weave Net integration with Kubernetes for seamless turn-up

This repo contains a Kubernetes add-on (a DaemonSet) to install
Weave Net with one command, and the source code for the image which
makes that happen.

## Prerequisites:

Kubernetes 1.4

## To use:

 * Bring up a Kubernetes cluster configured to use CNI. For example,
   using the [`kubeadm` command](http://kubernetes.io/docs/kubeadm/).

 * Install and run Weave Net as a DaemonSet:

```
kubectl create -f https://git.io/weave-kube
```

After a few seconds, one Weave Net pod should be running on each node,
and any further pods you create will be attached to the Weave network.

## Network Policy

As of 1.7.0, Weave Net supports the [Kubernetes policy
API](http://kubernetes.io/docs/user-guide/networkpolicies/) so that
you can securely isolate pods from each other based on namespaces and
labels.

## Changing configuration options

The URL https://git.io/weave-kube points to the latest release in this
repo; if you want to use a different version or to make changes to the
configuration just clone the repo and use the file
`weave-daemonset.yaml` directly.

## Alternative installation method

If you are using the older cluster set-up scripts from the kubernetes
repo, you specify CNI like this:

```
NETWORK_PROVIDER=cni cluster/kube-up.sh
```

## Known Issues

 * Does not automatically handle nodes being removed from the cluster.
   This won't cause issues in practice.

## Further Information

* [Weave Net Docs](https://www.weave.works/docs/net/latest/introducing-weave/)
* [Weave Net Source](https://github.com/weaveworks/weave)
