Role Name
=========

An Ansible role that installs/configures [PowerDNS] Recursor

Requirements
------------

Install required Ansible roles..  
````
sudo ansible-galaxy install -r requirements.yml
````

Role Variables
--------------

````
---
enable_pdns_recursor_fwd_zones: false  #defines if specific forward zones should be defined
install_pdns_recursor: true   #defines if recursive caching server is to be installed
pdns_download_url: 'https://downloads.powerdns.com/releases'
pdns_recursive_source_ip: false  #defines if source IP address should be defined for recursive queries...default is 0.0.0.0
pdns_recursor_fwd_zones:  #define forward lookup zone(s) along with DNS servers to use
  - name: 'blah.example.org'
    servers:
      - '192.168.1.5'
      - '192.168.1.6'
  - name: 'blah.blah.example.org'
    servers:
      - '192.168.2.5'
      - '192.168.2.6'
pdns_local_address: '0.0.0.0'
pdns_recursor_port: '5300'  #port pdns_recursor should listen on...default is 53 but needs to be changed to run both pdns services on same host
pdns_recursor_version: '3.7.1-1'
pri_dns: []  #defines primary dns server on network...define here or globally in group_vars/all
pri_domain_name: 'example.org'  #define here or globally in group_vars/all
sec_dns: []  #defines secondary dns server on network...define here or globally in group_vars/all
````

Dependencies
------------

Reference requirements section above...

Example Playbook
----------------

````
- hosts: all
  roles:
    - role: ansible-powerdns-recursor
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com

[PowerDNS]: <https://www.powerdns.com/>
