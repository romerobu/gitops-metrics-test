
## 1. Create Application charts

```bash
helm template . -f values-1.yaml --output-dir gitops-test-1-20
helm template . -f values-2.yaml --output-dir gitops-test-20-40
helm template . -f values-6.yaml --output-dir gitops-test-100-120

helm template . -f values-3.yaml --output-dir openshift-gitops-40-60
helm template . -f values-4.yaml --output-dir openshift-gitops-60-80
helm template . -f values-5.yaml --output-dir openshift-gitops-80-100
```

## 2. Apply resources

```bash
oc apply -f gitops-test-1-20/applications/templates/application.yaml &&
oc apply -f gitops-test-20-40/applications/templates/application.yaml &&
oc apply -f gitops-test-100-120/applications/templates/application.yaml &&
oc apply -f openshift-gitops-40-60/applications/templates/application.yaml &&
oc apply -f openshift-gitops-60-80/applications/templates/application.yaml &&
oc apply -f openshift-gitops-80-100/applications/templates/application.yaml
```

## 3. Delete resources

```bash
oc delete -f gitops-test-1-20/applications/templates/application.yaml &&
oc delete -f gitops-test-20-40/applications/templates/application.yaml &&
oc delete -f gitops-test-100-120/applications/templates/application.yaml &&
oc delete -f openshift-gitops-40-60/applications/templates/application.yaml &&
oc delete -f openshift-gitops-60-80/applications/templates/application.yaml &&
oc delete -f openshift-gitops-80-100/applications/templates/application.yaml
```

## 4. Delete namespaces

```bash
oc delete namespace app-{1..120}
```
