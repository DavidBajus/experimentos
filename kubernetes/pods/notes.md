# Notes


You can prepare yaml temple for kubernetes objects by dry-run.
example:
```
kubectl run busybox --image=busybox:1.28 --command sleep 5000  --dry-run=client -o yaml > testpod.yaml
```