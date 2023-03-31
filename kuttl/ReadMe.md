# KUTTL  -> https://kuttl.dev/

Let's try The Kubernetes Test Tool


# tun run tests (on existing kind cluster)
kubectl kuttl test --start-kind=false ./tests/e2e/

# tun run tests (create new kind cluster)
kubectl kuttl test --start-kind=false ./test/e2e/

# tun run tests (On Mocked cluster)
kubectl kuttl test --start-control-plane ./test/e2e/

# other useful flags
--kind-context (string)
--parallel (int)
--timeout (int)

# hint
More advanced assertions can be done with KubeAssert tool