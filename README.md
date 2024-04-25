# Kubewarden Fleet

This will deploy the essential Kubewarden stack packaged as Helm charts from the Kubewarden
Helm repo, https://charts.kubewarden.io, into the `cattle-fleet-system`
namespace. The defined Fleet modules have the chart dependencies codified via
`dependsOn`.

> Note: [cert-manager](https://cert-manager.io/docs/installation/) must be installed for the Kubewarden Controller to work.

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: kubewarden
  namespace: fleet-local
spec:
  repo: https://github.com/jordojordo/kubewarden-fleet.git
  branch: master
  paths:
    - kubewarden/

  # remove any external change done to resources owned by Fleet:
  correctDrift:
    enabled: true
    force: true
```
