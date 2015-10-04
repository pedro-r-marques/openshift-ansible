OpenContrail playbook role
==========================

This playbook installs opencontrail on k8s/openshift masters and nodes. It also (optionally)
installs a software gateway that provides connectivity between the underlay and the Public network
as well as connectivity between the internal underlay network where masters and minions are present
and a system network such as kube-system/default.

## User settings

### Per-host settings

Variable  | Description | Default 
----------|-------------|---------
opencontrail_interface | Physical interface used by the vrouter kernel module | eth0
opencontrail_ipaddr | IP address prefix | address of vhost0 when present, or the address of opencontrail_interface

### Global settings

Variables set in inventory file.

The inventory file should define a variable group such as:
```
[opencontrail:children]
masters
nodes
gateways

[opencontrail:vars]
opencontrail_public_subnet = 192.168.254.0/24
[...]
```

| Variable | Description | Default value |
|----------|-------------|---------------|
| opencontrail_public_subnet | IP subnet of the Public network | |
| opencontrail_http_proxy | Proxy used by docker builder | |
| opencontrail_dns_forwarder| DNS forwarder | |
| opencontrail_use_systemd | TODO: Use systemd to start docker containers | true |
| opencontrail_release | TODO: Software release to install | 2.20 |      

## Variables

|Variable | Description |
|---------| ---- |
| opencontrail_host_interface | |
| opencontrail_host_ipaddr | |
| opencontrail_host_address | |
| opencontrail_host_netmask | |
| opencontrail_host_gateway | |
| opencontrail_host_kernel_tag | |
| opencontrail_all_service_addresses | |
| opencontrail_all_release | |
| opencontrail_node_infra_gateway | |
| opencontrail_master_ifmap_port | 8444 (openshift) |

## Pre-requisites
ansible_facts:

openshift_facts:

global_vars:
  - master_address



