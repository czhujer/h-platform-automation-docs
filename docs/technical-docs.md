# technology stack

## supported platforms

### proxmox - LXC containers
- used in clusterless/standalone setup (server(s): hpa-pxmX)
- management through WebUI, REST API or pct util

### vmware - vcenter
- whole ecosystem for virtualization
- managed by terraform provider

## core system(s)

### C&C
- command and control server
- web server in golang

### terraform
- provisining tool

- https://github.com/czhujer/h-platform-automation-core/tree/master/tf-owncloud
- https://www.terraform.io/docs/index.html

### proxmox-provisioning-server
- https://github.com/czhujer/h-platform-automation-core/tree/master/proxmox-provisioning-server
- ruby web server with RestAPI

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

## LoadBalancer / central reverse-proxy server
- used nginx on hpa-pxm1
- config based on vhosts
- special locations for prometheus exporters
- monitoring over https://github.com/vozlt/nginx-module-vts

## provisioned systems / apps

### Owncloud

#### OS
- CentOS 7.x/8.x

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
