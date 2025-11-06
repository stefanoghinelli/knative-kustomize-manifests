# Knative operator upgrade steps

To upgrade the version from upstream:

```bash
helm repo add knative-operator https://knative.github.io/operator
helm repo update
helm search repo knative-operator/knative-operator # get the latest chart
helm pull knative-operator/knative-operator --version v1.19.5 --untar --untardir /tmp
```

Run the following command:

```bash
helm template knative-operator /tmp/knative-operator -n knative-operator --values MAINTENANCE.values.yaml > knative-operator-built.yaml
```

Check differences with the current manifests then update.

