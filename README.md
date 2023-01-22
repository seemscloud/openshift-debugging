# Openshfit Debugging

## After Installation / Upgrade

```bash
oc get clusterversion

oc get clusterversion -o json | jq -r '.items[].status.conditions[]'
```

```bash
oc get clusteroperators
```

```bash
oc adm must-gather
```

```bash
oc get api-resources

oc api-resources 2>&1  | grep -Ei "error.*" | grep -Po "[a-zA-Z0-9]*\.[a-zA-Z0-9]*\.[a-zA-Z0-9]*/[a-zA-Z0-9]*"
```

## Openshift Ingress

```bash
kubectl get ingresscontrollers \
  -n openshift-ingress-operator default
```

```bash
kubectl get pods \
  -n openshift-ingress

kubectl delete pods \
  -n openshift-ingress \
  -l ingresscontroller.operator.openshift.io/deployment-ingresscontroller=default \
  --force

kubectl logs \
  -n openshift-ingress \
  -l ingresscontroller.operator.openshift.io/deployment-ingresscontroller=default --follow
```
