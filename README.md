# H Platform Automation - Documentation

## basic schema

### v1
- first version, with customer modification (calculoid)
- supported "apps": owncloud
- supported infra (for apps):
  - lxc containers on proxmox
  - virtual machines on vmware vcenter 
- without dockerized owncloudstack
- without dockerized website (wordpress)
- without tracing
![Drag Racing](pics/HPA-overview-schema.png)

### v2
- dockerized owncloud-stack (systemd service with docker-compose, VM based on CoreOS)
- website (wordpress) in docker-compose mode (on virtual machine)
- added tracing (jaeger) in docker-compose mode (on virtual machine)

## status
- C&C server
  - not ready/work in progress
  - calculoid support
    - webhook calls are received on http layer and parsed
    - we need feature for calling jenkins server
  - missing vagrant support
  - missing IaC/server
- proxmox master
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - current setup supports only one master
  - unsupported proxmox VE version (for 5.4 support ended 31.7.2020)
  - lxc script is compatible only with old gem fog-proxmox (0.5.5 vs. 0.13.0)
- jenkins server
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - IaC don't cover jenkins plug-ins and jenkins jobs
  - not dockerized
- monitoring stack
  - https://github.com/czhujer/h-platform-automation-monitoring/issues
  - IaC don't cover bootstrap grafana DataSource and dashboards
  - not dockerized
  - based on (old) CentOS 7
- infrastructure (repo)
  - only support vagrant (with libvirt plugin)
  - planned terraform for Digital Ocean

## technical overview
[technical overview](docs/technical-docs.md)

