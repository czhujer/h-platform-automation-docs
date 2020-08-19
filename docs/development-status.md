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
  - IaC completely cover bootstrap proxmox VE
  - missing IaC for firewall
  - older debian (9) and unsupported proxmox VE version (5.4) 
  - missing PVE exporter (for prometheus)
  - v1 arch: setup supports only one master
 
## proxmox provisioning server
  - tracing support with opentracing-jaeger
  - compatible only with old (0.5.5) gem fog-proxmox, current 0.13.0
  - missing IaC for systemd unit
  - missing custom prometheus metrics
  - prometheus sdk auto-instrumentation

## HQ-server
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - jenkins server
    - IaC doesn't cover jenkins plug-ins and jenkins jobs
    - deprecated, will by erased
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
