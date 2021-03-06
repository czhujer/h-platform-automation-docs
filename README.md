# H Platform Automation - Documentation
modular PaaS solution (Platfrom as a service)

## basic description and schema

### v2
- standalone server(s) for front-end proxy (based of traefik) (T.B.A.)
- added proxmox-provisioning-server for lxc containers support
  - support for more proxmox servers/masters (T.B.A.)
- owncloud-stack based on LXC containers (proxmox) or Virtual Machines (vmare vcenter)
  - fully puppetize setup (include bootstrap owncloud and bootstrap owncloud users)
  - LAMP stack, based on Centos, configured over (masterless) Puppet & r10k
- dockerized owncloud-stack
  - systemd service in docker-compose (VM based on Fedora CoreOS)
  - provisioning over terraform (support libvirt+kvm)
  - support for C&C server (T.B.A.)
- main website based on wordpress) - docker-compose mode (on virtual machine)
- tracing based on jaeger - docker-compose mode (on virtual machine)
- monitoring based on prometheus and grafana
  - frontend proxy based on nginx
  - tracing support
- supported "apps": owncloud-stack
- jenkins server deprecated

high level diagram

![Drag Racing](pics/HPA-overview-schema-v2.png)


### v1
- first opensourced version
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

## technical overview
[technical overview](docs/technical-docs.md)

[development status](docs/development-status.md)

## details
[jenkins jobs](docs/jenkins-jobs-cs.md) v1 arch, inCzech

[monitoring](docs/monitoring-cs.md) (in czech)

[logging](docs/logging.md)

[c&c server](docs/c-and-c-server.md) (in czech)

[calculoid webook](docs/calculoid-webhook-url.md)

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

### message broker (testing purposes)
https://github.com/czhujer/h-platform-automation-message-broker/blob/master/README.md

## common info

### tracing
- https://speakerdeck.com/gianarb/distributed-tracing-faq

### security
- [DevSec Hardening Framework (https://dev-sec.io/)](https://dev-sec.io/)
    - https://github.com/dev-sec/linux-baseline
- https://securityhub.dev/
- https://github.com/joatmon08/tdd-infrastructure#built-in-policies

