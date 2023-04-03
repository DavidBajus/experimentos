# KUTTL  -> https://kuttl.dev/

Let's try The Kubernetes Test Tool

Tool for testing objects in kubernetes cluster just using yaml files. Tests can be run on existing king cluster or KUTTL will create kind cluster for you. There is one more option to use mocked control plane - more like integration testing, can be benefitial for faster testing of XRDs. 


# run commands examples:
## to run tests (on existing kind cluster)
```
kubectl kuttl test --start-kind=false ./tests/e2e/example-kind-test
```

## tun run tests (create new kind cluster)
```
kubectl kuttl test --start-kind=true ./tests/e2e/example-kind-test
```

## tun run tests (On Mocked cluster)
```
kubectl kuttl test --start-control-plane ./tests/e2e/example-mocked-test
```

# other useful flags
- --kind-context (string)
- --parallel (int)
- --timeout (int)

# hints
- More advanced assertions can be done with KubeAssert tool

- For running Mocked cluster need to have kubebuilder few tools installed: 
```
version=1.0.8 # latest stable version
arch=amd64

# download the release
curl -L -O "https://github.com/kubernetes-sigs/kubebuilder/releases/download/v${version}/kubebuilder_${version}_linux_${arch}.tar.gz"

# extract the archive
tar -zxvf kubebuilder_${version}_linux_${arch}.tar.gz
mv kubebuilder_${version}_linux_${arch} kubebuilder && sudo mv kubebuilder /usr/local/

# update your PATH to include /usr/local/kubebuilder/bin
export PATH=$PATH:/usr/local/kubebuilder/bin
```