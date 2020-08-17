# Monitoring

- over Prometheus, AlertManager, Grafana
- git repo: https://github.com/czhujer/h-platform-automation-monitoring


## zakladni info
Vetsina veci funguje jinak nez v zabbixu/nagiosu, jelikoz prometheus je navrzen na "chytrejsi" a skalovatelnejsi reseni. A spise patri do DevOps sveta.

Zakladni fungovani je, ze prometheus ma model pull, cili server si stahuje metriky v prislusnych URL (pres HTTP/HTTPS pouze)...

URL pak jsou endpointy aplikaci ci exportery/intergrace, ktere zprostredkovavaji metriky z veci styl linux, mysql server apod.

Namerene info jsou metriky, ktere maji labely a jine metadata.
Dotazovani je pak pres zjednoduseny jazyk PromQL (ala SQL).

Nad dotazy je pak alertmanager, ktery umi posleze "vyvolat" alarm a neco udelat (vetsinou poslat IM ci email).

Konfigurace serveru a cilovych stanic/exporters je pres puppet.. https://github.com/SugarFactory/puppet-prometheus/
seznam targets je pres pres File_SD.. viz odkaz nize..

Jenkins pak injektuje soubory s FQDN do adresare (na prom serveru), kam kouka prometheus service v ramci FIle_SD.

## links
- prometheus basic schema/workflow - https://prometheus.io/docs/introduction/overview/
- prometheus data model - https://prometheus.io/docs/concepts/data_model/
- prometheus exporters - https://prometheus.io/docs/instrumenting/exporters/
- prometheus - service discovery over file(s) - https://prometheus.io/docs/guides/file-sd/
- prometheus promQL - https://prometheus.io/docs/prometheus/latest/querying/basics/
- prometheus alerting - https://prometheus.io/docs/practices/alerting/

## komponenty

### prometheus

### prometheus exporters - used by HPA/APA
- https://github.com/prometheus/node_exporter
  puppet class
  - https://github.com/SugarFactory/puppet-prometheus/blob/master/manifests/node_exporter.pp
  - https://github.com/voxpupuli/puppet-prometheus/blob/master/manifests/node_exporter.pp
- https://github.com/prometheus/mysqld_exporter
- puppet https://github.com/SugarFactory/puppet-prometheus/blob/master/manifests/mysqld_exporter.pp
- https://github.com/hipages/php-fpm_exporter/releases
- https://github.com/Lusitaniae/apache_exporter/releases
- https://github.com/oliver006/redis_exporter/releases

### Grafana
- web gui pro zobrazovani info z data stores
- v APA primarne z promethea

- https://grafana.com/
- https://grafana.com/plugins
- https://grafana.com/dashboards
