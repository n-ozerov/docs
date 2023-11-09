To assign [public IP addresses](../../vpc/concepts/address.md#public-addresses) to [{{ managed-k8s-name }} nodes](../../managed-kubernetes/concepts/index.md#node-group), do one of the following:
* Specify `--network-interface ipv4-address=nat` or `--network-interface ipv6-address=nat`.
* [Enable access to {{ managed-k8s-name }} nodes from the internet](../../managed-kubernetes/operations/node-group/node-group-update.md#node-internet-access) after creating a node group.