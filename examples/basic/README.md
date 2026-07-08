# Basic Example

Minimal single-VNet Proxmox SDN example with host L3, SNAT, and dnsmasq DHCP enabled.

## What it creates

- SDN zone `hybzone` on bridge `vmbr0`.
- VNet `vnetmgmt` using VLAN ID `10`.
- Subnet `10.10.0.0/24` with gateway `10.10.0.1`.
- DHCP range `10.10.0.120` through `10.10.0.220`.
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
- `proxmox_node`
- `proxmox_host`

## Outputs

- `zone_name`: Created SDN zone name.
- `vnets`: Created Proxmox SDN VNets.
- `subnets`: Created Proxmox SDN subnets with DHCP metadata.
