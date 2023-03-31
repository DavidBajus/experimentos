# KUTTL  -> https://kuttl.dev/

Let's try The Kubernetes Test Tool


# tun run tests (on existing kind cluster)
kubectl kuttl test --start-kind=false ./tests/e2e/

# tun run tests (create new kind cluster)
kubectl kuttl test --start-kind=true ./test/e2e/

# tun run tests (On Mocked cluster)
kubectl kuttl test --start-control-plane ./test/e2e/

# other useful flags
--kind-context (string)
--parallel (int)
--timeout (int)

# hint
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