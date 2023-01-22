# Openshfit Debugging

## Install Status

#### General

```bash
oc get clusterversion

oc get clusterversion -o json | jq -r '.items[].status.conditions[]'
```

```bash
oc get clusteroperators.config.openshift.io

oc get clusteroperators.config.openshift.io openshift-apiserver -o yaml | grep "not ready" -A1
```

```bash
oc api-resources

oc api-resources 2>&1  | grep -Ei "error.*" | grep -Po "[a-zA-Z0-9]*\.[a-zA-Z0-9]*\.[a-zA-Z0-9]*/[a-zA-Z0-9]*"
```

#### Gahter Logs

```bash
oc adm must-gather
```

```bash
openshift-install gather bootstrap --dir install_dir/

openshift-install gather bootstrap \
  --dir install_dir/ \
  --bootstrap bootstrap-0.seems.cloud \
  --master master-0.seems.cloud \
  --master master-0.seems.cloud \
  --master master-0.seems.cloud
```

#### Ignition Files

```bash
oc get machineconfigpools
oc get machineconfig
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
