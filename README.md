# zsel-infrastructure: Physical Hardware Layer

**Purpose**: On-premises hardware infrastructure documentation and IaC - servers, power, cooling, disaster recovery

**Part of**: [ZSEL 7-Layer Architecture](../SERWERY/docs/ARCHITECTURE.md)

## Overview

Physical infrastructure for ZSEL:
- **Hardware Specifications**: 8× Mac Pro M2 Ultra servers
- **Kubernetes Cluster**: K3s with 17 nodes (1 control + 16 compute)
- **Storage**: 64TB distributed storage
- **Compute**: 512 CPU cores, 1.5TB RAM
- **Infrastructure as Code**: Terraform for reproducibility

## Hardware Specifications

### Mac Pro M2 Ultra Servers
```
Quantity:           8 units
Processor:          Apple M2 Ultra (20 cores: 16 P-cores + 4 E-cores)
Memory:             192GB unified memory per unit
Storage:            4TB internal SSD (+ external 8TB per unit)
Network:            10Gbps Ethernet with LAG (Link Aggregation Group)
Power:              2× 1600W power supplies per unit
Cooling:            Passive air cooling
```

### Cluster Configuration
```
Total Nodes:        17 (1 control plane + 16 compute)
Total Cores:        320 CPU cores (16 P-cores × 8 units × 2.5)
Total Memory:       1.5TB RAM
Total Storage:      64TB (8TB × 8 units)
Uptime:             26+ days
Network:            Cilium CNI with eBPF
Storage:            Longhorn distributed storage
```

## Directory Structure

```
zsel-infrastructure/
├── hardware/
│   ├── mac-pro-specs.md       Mac Pro M2 Ultra specifications
│   ├── network-connectivity.md Network interface configuration
│   └── storage-layout.md       Storage attachment and partitioning
├── network/
│   └── network-topology.md     Network diagram and CIDR allocation
├── power/
│   ├── power-distribution.md   PDU configuration, load balancing
│   ├── cooling-plan.md         Room cooling, thermal management
│   └── ups-configuration.md    Uninterruptible power supplies
├── documentation/
│   ├── MAINTENANCE.md          Regular maintenance procedures
│   ├── FAILOVER.md             Failover procedures
│   └── CAPACITY_PLANNING.md    Expanding capacity, adding nodes
├── terraform/
│   ├── variables.tf            Infrastructure variables
│   ├── main.tf                 Main infrastructure definition
│   └── outputs.tf              Output values
└── README.md                   This file
```

## Hardware Specifications

See [hardware/mac-pro-specs.md](hardware/mac-pro-specs.md) for:
- Processor specifications
- Memory configuration
- Storage details
- Power requirements
- Cooling specifications

## Network Connectivity

See [hardware/network-connectivity.md](hardware/network-connectivity.md) for:
- 10Gbps Ethernet configuration
- Link aggregation (LAG) setup
- DNS configuration
- Firewall rules

## Storage Layout

See [hardware/storage-layout.md](hardware/storage-layout.md) for:
- Internal SSD configuration
- External storage attachment
- Longhorn volume provisioning
- Backup storage location

## Power & Cooling

See [power/](power/) for:
- **Dual 1600W PSUs** per Mac Pro
- **PDU load balancing** on 400A feeds
- **Passive air cooling** design
- **UPS 15-minute hold** time

## Maintenance

See [documentation/MAINTENANCE.md](documentation/MAINTENANCE.md) for:
- Monthly health checks
- Quarterly deep cleaning
- Annual component inspections
- Database optimization

## Disaster Recovery

See [documentation/FAILOVER.md](documentation/FAILOVER.md) for:
- Node failure procedures
- Cluster recovery
- Data restoration
- RTO/RPO targets

## Capacity Planning

See [documentation/CAPACITY_PLANNING.md](documentation/CAPACITY_PLANNING.md) for:
- Current utilization metrics
- Growth projections
- When to add nodes
- Hardware procurement process

## Infrastructure as Code

### Variables
See [terraform/variables.tf](terraform/variables.tf) for configurable parameters:
- Node count
- Resource allocations
- Storage sizes
- Network CIDR blocks

### Deployment
```bash
# Initialize Terraform
terraform init

# Plan changes
terraform plan

# Apply configuration
terraform apply

# Destroy infrastructure (CAUTION)
terraform destroy
```

## Monitoring

Monitor hardware health:
```bash
# Node status
kubectl get nodes -o wide

# Resource usage
kubectl top node

# Hardware temperatures
kubectl get events

# Storage status
kubectl get pvc -A
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- Hardware documentation standards
- Terraform code style
- Testing infrastructure changes

## License

MIT License - See [LICENSE](LICENSE)

---

**Maintainers**: Infrastructure Team  
**Last Updated**: March 11, 2026
