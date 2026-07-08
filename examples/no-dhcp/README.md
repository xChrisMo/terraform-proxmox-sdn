# No DHCP Example

Single-VNet Proxmox SDN example with host L3 and SNAT enabled, but DHCP disabled.

Use it when guests should use static IP addresses or when DHCP is provided by another system.

## What it creates

- SDN zone `statzone` on bridge `vmbr0`.
- VNet `vstatic` using VLAN ID `100`.
- Subnet `10.100.0.0/24` with gateway `10.100.0.1`.
- Host-side L3 gateway configuration.
- SNAT through uplink interface `vmbr0`.
- No dnsmasq DHCP range.

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
- `subnets`: Created Proxmox SDN subnets.
