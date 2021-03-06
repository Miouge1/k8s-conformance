## To reproduce:

This Kubernetes conformance report is generated by [Konvoy](https://docs.d2iq.com/ksphere/konvoy/).

### Provision the Kubernetes cluster

To recreate these results, you need to provision a Kubernetes cluster using Konvoy.
To do so, please run the following command:

```bash
$ konvoy up --provisioner=aws
```

Once Konvoy finishes the installation, but before running conformance tests, it is necessary to open TCP ports 30000-32767 on all worker nodes in AWS console and then proceed to run the conformance tests.

We have raised [an issue](https://github.com/kubernetes/kubernetes/issues/90764) to address it, as we belive that having these ports blocked by default is a security feature.

### Run conformance tests

Tests are run according to the [official instructions](https://github.com/cncf/k8s-conformance/blob/master/instructions.md):
* download sonobuoy v0.19.0
* `sonobuoy run --mode=certified-conformance`
* `sonobuoy retrieve`
* `sonobuoy delete`

### Clean-up

To delete the entire infrastructure, please run the following command:

```bash
$ konvoy down
```
