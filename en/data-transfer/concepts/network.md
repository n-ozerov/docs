# Network in {{ data-transfer-full-name }}

When creating an endpoint, you can select a [cloud network](../../vpc/concepts/network.md) and [security groups](../../vpc/concepts/security-groups.md) for network traffic. If the VMs and DB clusters used in endpoints are hosted in the selected cloud network, the rules of the selected security groups will apply to them during a transfer. This lets you perform transfers without changing the rules for the existing security groups of your VMs or DB clusters.

If you need to migrate data between {{ yandex-cloud }} and a third-party cloud, add rules to the endpoint cluster security group, which allow incoming connections to it from the internet from [IP addresses used by {{ data-transfer-name }}](https://stat.ripe.net/widget/announced-prefixes#w.resource%3DAS200350%26w.min_peers_seeing%3D0).

## Subnet IP address ranges {#subnet-address-ranges}

When performing transfers between the source and target hosts that are in different subnets within {{ yandex-cloud }}, their IP address ranges should not overlap. For example, an error occurs if the hosts use subnets with the following IP ranges:

* `network-1/subnet-a` with the IPv4 CIDR `10.130.0.0/24`.
* `network-2/subnet-b` with the IPv4 CIDR `10.130.0.0/24`.