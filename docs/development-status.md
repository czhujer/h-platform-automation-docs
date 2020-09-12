# development status (of components)
## apps
### owncloud-stack
  - VM, LXC
    - based on Centos 7
    - Mysql server 5.x, PHP-FPM 7.x, Apache, Redis
    - prometheus exporters (node, apache, mysql, ..)
  - DOCKER
    - based on owncloud images (mariadb)
    - added node and cadvisor exporters

## common
  - missing support for php-opcache exporter

## C&C server
  - not ready/under development
  - calculoid webhook support (v1 arch)
    - only basic functionality
    - webhook calls are received on http layer and parsed
    - missing calling jenkins server
    - some TODOs in code     
  - only basic jaeger support
  - only auto-instrumented prometheus
  - endpoint for proxmox-provisioning-server (v2 arch) has several TODOs
  - prometheus target management
    - add handler for adding targets
    - adding targets has several TO-DOs
    - missing handler/code for Removing targets
  - missing features
    - api endpoint and calling terraform
    - api endpoint and calling jenkins server (v1 arch compat)
    - api endpoint and calling dns handler (v1 arch compat)
    - detailed prometheus monitoring
    - better jaeger tracing
    - html templating
    - swagger support
  - missing vagrant support
  - missing CI/CD pipelines for testing and docker builds

## proxmox master
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - IaC completely cover bootstraping proxmox VE
  - missing IaC for firewall
  - older debian (9) and unsupported proxmox VE version (5.4) 
  - missing (prometheus) PVE exporter
  - v1 arch: setup supports only one master

## proxmox provisioning server
  - tracing support with opentracing-jaeger
  - compatible only with old (0.5.5) gem fog-proxmox, current 0.13.0
  - implemented prometheus sdk auto-instrumentation
  - missing IaC for budler (gems) install
  - missing custom prometheus metrics

## HQ-server
  - https://github.com/czhujer/h-platform-automation-cm/issues
  - not dockerized nginx
  - several TO-DOs in IaC code

## monitoring stack
  - https://github.com/czhujer/h-platform-automation-monitoring/issues
  - IaC don't cover bootstrap grafana DataSource and dashboards
  - not dockerized
  - based on (old) CentOS 7

## tracing stack
  - dockerized (docker 19.03 on Ubuntu 20.04 LTS)
  - basic setup with jaeger 1.18
  - elasticsearch server for jaeger backend

## front-end proxy
  - only basic setup with traefik

## infrastructure (repo)
  - support vagrant with libvirt plugin
  - planned terraform for Digital Ocean
