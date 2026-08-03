# External Gateway with Bonded Interface

This directory contains the configuration to set up an external gateway in Harvester using Kube-OVN with a bonded interface for high availability and performance.

## Prerequisites

- Two physical interfaces available on your Harvester nodes (e.g., `ens19` and `ens20`).
- Harvester cluster running with Kube-OVN.

## Usage

1. Create the ClusterNetwork and VlanConfig to set up the bonded interface (`ext-bond-br`):
   ```bash
   kubectl apply -f 00_clusternetwork.yaml
   ```

2. Verify the ClusterNetwork and VlanConfig are created and ready.

3. Apply the rest of the manifests to set up the NetworkAttachmentDefinitions, VPC, ProviderNetwork, and subnets:
   ```bash
   kubectl apply -f 01_nad.yaml
   kubectl apply -f 02_vpc.yaml
   kubectl apply -f 03_provider-vlan.yaml
   kubectl apply -f 04_subnet-internal.yaml
   kubectl apply -f 05_subnet_external.yaml
   ```

4. Proceed with setting up NAT and EIP as needed using the remaining manifests.
