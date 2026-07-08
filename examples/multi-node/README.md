# Multi-Node Example

Current single-node implementation shaped around a future Proxmox cluster SDN pattern.

The active configuration manages node 1 only. The commented node 2 block documents the intended direction for a later multi-node module release.

## What it creates

- SDN zone `clust01` on bridge `vmbr0`.
- VNet `vclst01m` using VLAN ID `200`.
- Subnet `10.200.0.0/24` with gateway `10.200.0.1`.
- DHCP range `10.200.0.120` through `10.200.0.220`.
- SNAT through uplink interface `vmbr0`.

## Usage

```bash
cp terraform.tfvars.example terraform.tfvars
terraform init
terraform plan
terraform apply
```

Edit `terraform.tfvars` before running `terraform plan`.

## Required Variables

- `proxmox_url`
- `proxmox_token`
- `proxmox_node1`
- `proxmox_host_node1`

## Optional Variables

- `proxmox_node2`: Placeholder for the planned secondary node example.
- `proxmox_host_node2`: Placeholder for the planned secondary node SSH host.

## Outputs

- `sdn_nodes`: Aggregated SDN outputs for the active node configuration.
