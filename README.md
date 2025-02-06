# kubernetes

control plane nodes and worker nodes

containers must be inside pod. In pod there can be 1 or more containers but in general odd numbers are better in kubernetes.

Pod is shared execution env and shared execution env is basically collection of things app needs to run.

scaling in kubernetes is about adding removing pods, not about adding contatiners into pod

pod life cycle: PENDING, RUNNING, SUCCEEDED/FAILED
