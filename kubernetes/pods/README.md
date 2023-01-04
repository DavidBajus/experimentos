# Notes


You can prepare yaml template for kubernetes objects by dry-run.
example:
```
kubectl run busybox --image=busybox:1.28 --command sleep 5000  --dry-run=client -o yaml > testpod.yaml
```


Check logs of init container:
kubectl logs busybox -c init-create-folder
