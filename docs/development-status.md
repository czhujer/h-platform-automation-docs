# development status (of components)

## C&C server
  - not ready/under development
  - calculoid support (v1 arch)
    - webhook calls are received on http layer and parsed
    - we need feature for calling jenkins server
  - missing REST API
    - endpoint for calling jenkins server (v1 arch)
    - endpoint for calling dns handler (v1 arch)
    - endpoint for calling terraform
    - endpoint for calling proxmox-provisioning-server (v2 arch)
  - missing vagrant support
  - missing IaC/server (probably on HQ-server)

## proxmox master
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - v1 arch setup supports only one master
  - IaC completely cover bootstrap proxmox VE
  - missing IaC for firewall
  - older debian (9) a unsupported proxmox VE version (5.4) 
  - lxc script is compatible only with old gem fog-proxmox (0.5.5 vs. 0.13.0)
  - missing PVE exporter (for prometheus)

## HQ-server
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - jenkins server
    - IaC doesn't cover jenkins plug-ins and jenkins jobs
  - dns handling (over jenkins jobs)
    - missing IaC
  - missing IaC for firewall
  - not dockerized
  - based on (old) CentOS 7

## monitoring stack
  - https://github.com/czhujer/h-platform-automation-monitoring/issues
  - IaC don't cover bootstrap grafana DataSource and dashboards
  - not dockerized
  - based on (old) CentOS 7
## tracing stack
  - dockerized (docker 19.03 on Ubuntu 20.04 LTS)
  - basic setup with jaeger 1.18
  - elasticsearch server like jaeger backend
## infrastructure (repo)
  - only support vagrant (with libvirt plugin)
  - planned terraform for Digital Ocean
