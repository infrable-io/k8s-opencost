# K8s OpenCost

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/infrable-io/terraform-aws-static-website/blob/master/LICENSE)
[![Maintained by Infrable](https://img.shields.io/badge/Maintained%20by-Infrable-000000)](https://infrable.io)

k8s-opencost installs [OpenCost](https://www.opencost.io), a vendor-neutral open source project for measuring and allocating infrastructure and container costs in Kubernetes environments. OpenCost provides the cost allocation engine used by [Kubecost](https://www.kubecost.com), a commerical product.

This Helm chart captures the OpenCost installation steps documented [here](https://www.opencost.io/docs/install) in code.

## Installation

### From Source

```bash
$ git clone git@github.com:infrable-io/k8s-opencost.git
$ cd k8s-opencost
$ kubectl create namespace opencost
$ helm install opencost . --namespace opencost
```

## Testing

To test the Helm chart, run the following:

```bash
$ helm test opencost --namespace opencost
```

## Helm chart dependencies

Helm charts store their dependencies in `charts/`. For chart developers, it is often easier to manage dependencies in `Chart.yaml`, which declares all dependencies.

The `dependency` commands (`build`, `list`, `update`) operate on that file, making it easy to synchronize between the desired dependencies and the actual dependencies stored in the `charts/` directory.

For example, this `Chart.yaml` declares a single dependency:
* prometheus

```yaml
dependencies:
  - name: prometheus
    version: "15.14.0"
    repository: https://prometheus-community.github.io/helm-charts
    condition: prometheus.enabled
```
