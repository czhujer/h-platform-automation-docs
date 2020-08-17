# H Platform Automation - Documentation

## basic schema

### v1
- first version
- with customer modification (calculoid)
- supported "apps": owncloud
- supported infra (for apps):
  - lxc containers on proxmox
  - virtual machines on vmware vcenter 
- CI/CD based on jenkins server
- monitoring based on prometheus and grafana

- without dockerized owncloudstack
- without dockerized website (wordpress)
- without tracing

high level diagram
![Drag Racing](pics/HPA-overview-schema.png)

### v2
- added dockerized owncloud-stack (systemd service with docker-compose, VM based on CoreOS)
- added website (wordpress) in docker-compose mode (on virtual machine)
- added tracing (jaeger) in docker-compose mode (on virtual machine)
- jenkins server will be deprecated

## status
- C&C server
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
- proxmox master
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - v1 arch setup supports only one master
  - IaC completely cover bootstrap proxmox VE
  - missing IaC for firewall
  - older debian (9) a unsupported proxmox VE version (5.4) 
  - lxc script is compatible only with old gem fog-proxmox (0.5.5 vs. 0.13.0)
  - missing PVE exporter (for prometheus)
- HQ-server
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - jenkins server
    - IaC doesn't cover jenkins plug-ins and jenkins jobs
  - dns handling (over jenkins jobs)
    - missing IaC
  - missing IaC for firewall
  - not dockerized
  - based on (old) CentOS 7
- monitoring stack
  - https://github.com/czhujer/h-platform-automation-monitoring/issues
  - IaC don't cover bootstrap grafana DataSource and dashboards
  - not dockerized
  - based on (old) CentOS 7
- tracing stack
  - dockerized (docker 19.03 on Ubuntu 20.04 LTS)
  - basic setup with jaeger 1.18
  - elasticsearch server like jaeger backend
- infrastructure (repo)
  - only support vagrant (with libvirt plugin)
  - planned terraform for Digital Ocean

## technical overview
[technical overview](docs/technical-docs.md)

## repositories

### core
https://github.com/czhujer/h-platform-automation-core/blob/master/README.md

### cm
https://github.com/czhujer/h-platform-automation-cm/blob/master/README.md

### website
https://github.com/czhujer/h-platform-automation-website/blob/master/README.md

### monitoring
https://github.com/czhujer/h-platform-automation-monitoring/blob/master/README.md

### tracing
https://github.com/czhujer/h-platform-automation-tracing/blob/master/README.md

### C&C server (unde development)
https://github.com/czhujer/h-platform-automation-cc-server/blob/master/README.md

## message broker (testing purposes)
https://github.com/czhujer/h-platform-automation-message-broker/blob/master/README.md
