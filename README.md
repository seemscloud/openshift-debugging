# Openshfit Debugging

## After Installation / Upgrade

```bash
oc get clusterversion

oc get clusterversion -o json | jq -r '.items[].status.conditions[]'
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
