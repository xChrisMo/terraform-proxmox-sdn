# Six VLAN Reference Example

Six-network Proxmox SDN example for a production-style segmented environment.

## What it creates

- SDN zone `hybzone` on bridge `vmbr0`.
- Six VLAN-backed VNets:
  - `vnetmgmt` on VLAN `10` for management.
  - `vnetobs` on VLAN `11` for observability.
  - `vnetdev` on VLAN `20` for development.
  - `vnetstag` on VLAN `30` for staging.
  - `vnetprod` on VLAN `40` for production.
  - `vnetlab` on VLAN `50` for validation and testing.
- A `/24` subnet per VNet with the `.1` address as the gateway.
- DHCP ranges from `.120` through `.220` in each subnet.
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
