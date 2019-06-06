ovirt-vm-operator
====================

Operator which deploy virtual machine from oVirt/RHV to kubernetes

# Installation
```bash
kubectl create -f deploy/crds/ovirt_v1alpha1_ovirtvm_crd.yaml
kubectl create -f deploy/service_account.yaml
kubectl create -f deploy/role.yaml
kubectl create -f deploy/role_binding.yaml
kubectl create -f deploy/operator.yaml
```

# Migrate apache VM from oVirt to kubernetes
```bash
cat deploy/crds/ovirt_v1alpha1_ovirtvm_cr.yaml
apiVersion: ovirt.kubevirt.io/v1alpha1
kind: OvirtVm
metadata:
  name: ovirt_apache
  namespace: default
spec:
  vm_name: apache
  ovirt_fqdn: my.ovirt.org
  ovirt_username: admin@internal
  ovirt_password: password
```

Check it's created

```bash
kubectl get vm
```

# Troubleshooting

```bash
kubectl logs deploy/ovirt-vm-oprator -c ansible
```
