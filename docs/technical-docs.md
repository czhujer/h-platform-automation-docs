# technology stack

## supported platforms

### proxmox - LXC containers
- used in clusterless/standalone setup (Server(s): hpa-pxmX)
- currently old stable, in future will be deprecated (for this project)
- management through WebUI, REST API or pct util

### vmware - vcenter
- whole ecosystem for virtualization
- managed by terraform provider

## CI/CD system - jenkins
###jenkins
- task/build server
- https://jenkins.io/doc/tutorials/
- https://jenkins.io/doc/
- for creating and management provisioned appliances/stacks
  - creating over terraform/scripts, configuration over "puppet apply"
- for jenkins server management itself

jenkins basics:
- basic tasks/objects are jobs
- plugins for extented features
- in HPA most actions in jobs are based on "execute shell"

- main used plugins:
  - slave plugin - for running jobs on proxmox master
    - control over labels
    - https://wiki.jenkins.io/display/JENKINS/SSH+Slaves+plugin
  - multijob plugin - https://wiki.jenkins.io/pages/viewpage.action?pageId=59510168
  - conditonal builds (here for DNS records management) - https://plugins.jenkins.io/conditional-buildstep
  - artifacts - transfer info (VM/container ID/, IP address etc betwwen jobs) - https://wiki.jenkins.io/display/JENKINS/Copy+Artifact+Plugin

## core management "plugins"
### terraform
- https://www.terraform.io/docs/index.html

### ruby script/wrapper for lib-fog
- T.B.A.

## Config Management

### Puppet, r10k
- environment for Config Management - https://en.wikipedia.org/wiki/Configuration_management
- https://docs.google.com/presentation/d/1WxWL3GolxDvRY2CVanm0My8CxWiHwZYesJqAmRm6JFU/edit?usp=sharing
- written in ruby, currently used in this platform : v5.5
- main docs - https://puppet.com/
- secrets/vars over hiera - https://puppet.com/docs/puppet/5.5/hiera_intro.html
- modules - https://puppet.com/docs/puppet/5.5/modules_fundamentals.html
- market for modules - puppet forge - https://forge.puppet.com/
- modules management over tool r10k - https://github.com/puppetlabs/r10k

### rspec-puppet
- framework for testing puppet code/modules
- based on rspec framework for ruby
- https://rspec-puppet.com/

### serverspec tests
- future
- tests pro infrastrucre/servers in general
- https://serverspec.org

## git / gitolite
- for versioning :)
- git - https://git-scm.com/

## DNS
- old-stable domain: hcloud.cz
- management over mysql server (direct SQL insert/delete)
- for czechia/regzone.cz management over API -> script: dns_modify_regzone.php
- usage: php dns_modify_regzone.php --login-name "${login_name}" --login-password "${login_password}" --record-name "oc-333" --action insert --record-ip "${ip_address}"

## LoadBalancer / central reverse-proxy server
- used nginx on hpa-pxm1
- config based on vhosts
- special locations for prometheus exporters
- monitoring over https://github.com/vozlt/nginx-module-vts

## provisioned systems / apps

### Owncloud

#### OS
- CentOS 7.x

#### web server
Apache

#### PHP
- version 7.1
- Opcache, APCu, pecl extensions..

#### PHP-FPM
- for running PHP scripts

#### Mysql
- main database platform/server

#### Redis
- in-memory storage.. very f*** fast..
- used for php sessions, non-persitent (external) cache (PHP,..)

#### App - Owncloud
- basic bootstrap over puppet modul (https://github.com/shoekstra/puppet-owncloud)
- this modul are solving basic configuration - /var/www/html/owncloud/config/autoconfig.php
- puppet file_line is used for other config parameters in /var/www/html/owncloud/config.php
- puppet exec is used for run occ util for rest of configuration - lang, cron, apps, market,..
- docs:
  - https://doc.owncloud.org/server/10.1/admin_manual/
  - https://github.com/owncloud/docs/tree/master/modules/admin_manual/pages/installation
  - https://github.com/owncloud/docs/tree/master/modules/admin_manual/pages/configuration
  - upgrades - https://doc.owncloud.com/server/admin_manual/configuration/server/occ_command.html#example-commands
  - trusted domains - https://doc.owncloud.org/server/9.0/admin_manual/configuration_server/config_sample_php_parameters.html#default-parameters
