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

high level diagram

T.B.A.

## technical overview
[technical overview](docs/technical-docs.md)

[monitoring](docs/monitoring-cs.md) (in czech)

[development status](docs/development-status.md)

[logging](docs/logging.md)

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
