# nats-helm-subpackaged

This is an example of using the NATS helm chart as a sub-package allowing arbitrarily complex k8s deployment manifest.

## Big idea

Leaverage the NATS helm chart in the context of a larger (and more complicated) k8s deployment,
e.g. configuring load balancer services and other environment specific setups that are not directly
part of the NATS helm chart.

### Chart.yaml dependency

Note that the NATS helm chart added as a dependency in `Chart.yaml`. This is a mechanism (and a responsibility) to
set a specific version of the NATS helm chart in your project.

### values.yaml

Note the namespace nesting in `values.yaml` (an additioinal `nats:` indention) that reflects subpackage.

## This chart

For demonstration:

- Adds a load balancer service, `templates/services-lb.yaml`, that exposes the NATS listener (and monitor)
to k8s-external clients
- Specifies a specific NATS release in `values.yaml`

### Deployment

`helm install -f values.yaml <deploy name> .`

## See also

- [NATS Helm Chart repo: "Using NATS chart as dependency"](https://github.com/nats-io/k8s/tree/main/helm/charts/nats)