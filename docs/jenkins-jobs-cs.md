
# jenkins jobs workflow

- aktualne ctyri hlavni multijoby (zacinaji cislem - kvuli odliseni a poradi)
  - 0.run-multijob-for-create-owncloud-b2c-container - vytvareni owncloudu serveru na LXC kontejneru
  - 1.run-multijob-for-create-owncloud-virtual-machine - vytvareni Owncloud serveru na (vmware) virtualnim serveru
  - 99.run-multijob-for-delete-owncloud-b2c-container - mazani owncloud serveru na LXC kontejneru
  - 98.run-multijob-for-delete-owncloud-virtual-machine - mazani Owncloud serveru na (vmware) virtualnim serveru

- v multijobech je spusteni dalsich jobs

## 0.run-multijob-for-create-owncloud-b2c-container

  - create-owncloud-b2c-container
    - vytvoreni lxc kontejneru na proxmox serveru
    - pres shell se zavola ruby script pxm-create-container.rb (pres knihovnu fog) a ten zavola proxmox API
      - skript funguje tak, ze prvne ypise stavajici kontejnery, zjisti nejvyssi ID, to inkrementuje a odvodi z neho IP adresu
      - posleze se jeste propise promenna pro velikost root disku, vygeneruje se root heslo a zavola se create funkce
    - zvolena velikost disku a vygenerova id/ct_id se ulozi do souboru export_props.properties
    - soubor export_props.properties se pak exportuje jako artifacts do jenkins serveru

  - setup-owncloud-b2c-container
    - nakopirovani a spusteni bootstrap skripts pro oziveni ruby a puppetu
    - instalace puppet modules pres r10k z Puppetfile r10k-puppetfiles\Puppetfile-owncloudstack
    - vygenerovani hiera configu a souboru s heslama (pro puppet vars) pres skript hiera-items-handler.pl
    - nakopirovani a aplikace puppet manifests -> vytvoreni a konfigurace software stacku

  - fix-oc-config-in-b2c-container
    - uprava owncloud configu.. trusted domains..
  
  - bootstrap-oc-users-in-b2c-container
    - vytvoreni users a zarazeni do groups (perl skript bootstrap_oc_users.pl)

  - create-dns-record-for-owncloud-b2c
    - vytvoreni DNS (A) zaznamu (pro cust.h-software.cz) pres primy zapis pres SQL do mysql serveru (ptproxy), na ktery jsou napojene DNS servery pro (sub)domenu cust.h-software.cz, plus kontrola existujiciho zaznamu

  - create-nginx-vhost-for-owncloud-b2c
    - vygenerovani puppet manifestu pro konkretni nginx vhost na hpa-pxm1
    - vygenerovani pres bash template v configs-servers\nginx-vhosts-generator\puppet-nginx-vhost.pp.template

  - run-puppet-apply-locally
    - applikace puppet manifests (na hpa-pxm1), aby se uvedl v zivot nginx vhost vygenerovan jobem create-nginx-vhost-for-owncloud-b2c

  - add-ct-target-to-prometheus-file-sd
    - zavolani ssh commandu na prometheus serveru pro pridani files pro File_SD s target URL

## 1.run-multijob-for-create-owncloud-virtual-machine

  - create-owncloud-virtual-machine
    - vytvoreni virtualniho stroje na vmware clusteru/vcenter pres terraform
    - prvne se vylistuji stavajici soubory s TR vars (oc-30x.trvars), zjisti se IDcko dalsi virtualky
    - dle toho se vygeneruje soubor s TR vars, kde je nazev virtualky, IP adresa a velikost data disku
    - posleze se spusti prikazy terraform plan a terraform apply (ktere vola vmware API) a vytvori virtualni stroj (vc. nastaveni IP adresy, GW, DNS resolvers)

  - create-dns-record-for-owncloud-virtual-machine
    - analogicka/stejna funkcnost jako create-dns-record-for-owncloud-b2c
    - vytvoreni DNS (A) zaznamu (pro cust.h-software.cz) pres primy zapis pomoci SQL do mysql serveru (ptproxy), na ktery jsou napojene DNS servery pro (sub)domenu cust.h-software.cz, plus kontrola existujiciho zaznamu

  - create-dns-record2-for-owncloud-virtual-machine
    - vytvoreni DNS (A) zaznamu pro domenu ceskycloud.cz (a pripadne dalsi) pres API regzone.cz pomoci PHP skriptu dns_modify_regzone.php

  - setup-owncloud-virtual-machine
    - nakopirovani a spusteni bootstrap skripts pro oziveni ruby a puppetu
    - instalace puppet modules pres r10k z Puppetfile r10k-puppetfiles\Puppetfile-owncloudstack
    - vygenerovani hiera configu a souboru s heslama (pro puppet vars) pres skript hiera-items-handler.pl
    - nakopirovani a aplikace puppet manifests -> vytvoreni a konfigurace software stacku

  - fix-oc-config-in-virtual-machine
    - uprava owncloud configu.. trusted domains..

  - bootstrap-oc-users-in-virtual-machine
    - vytvoreni users a zarazeni do groups (perl skript bootstrap_oc_users.pl)

  - change-password-in-virtual-machine
    - zmena root hesla (pres ssh command)

  - create-nginx-vhost-for-owncloud-virtual-machine
    - vygenerovani puppet manifestu pro konkretni nginx vhost na hpa-pxm1
    - vygenerovani pres bash template v configs-servers\nginx-vhosts-generator\puppet-nginx-vhost.pp.template

  - run-puppet-apply-locally
    - applikace puppet manifests (na hpa-pxm1), aby se uvedl v zivot nginx vhost vygenerovan jobem create-nginx-vhost-for-owncloud-b2c

  - add-vm-target-to-prometheus-file-sd
    - zavolani ssh commandu na prometheus serveru pro pridani files pro File_SD s target URL

## 98.run-multijob-for-delete-owncloud-virtual-machine

  - delete-owncloud-virtual-machine

  - delete-dns-record-for-owncloud-b2c

  - delete-dns-record2-for-owncloud-virtual-machine

  - delete-nginx-vhost-for-owncloud-b2c

  - run-puppet-apply-locally

  - remove-target-to-prometheus-file-sd

## 99.run-multijob-for-delete-owncloud-b2c-container

  - delete-owncloud-b2c-container

  - delete-dns-record-for-owncloud-b2c

  - delete-nginx-vhost-for-owncloud-b2c

  - run-puppet-apply-locally

  - remove-target-to-prometheus-file-sd
