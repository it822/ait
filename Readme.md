## Welcome to the AIT lab
### This repo contains files used to build out the lab environment
#### we use kvm, qemu, libvirt, vlan, ansible, virsh, agama and cloudinit to build out the lab infrastructure
##### virtual machines used for building out the lab are:
###### 1. openvpn on fedora
###### 2. rancher AI on suse linux
###### 3. harvester on sle micro with elemental
###### 4. suse manager on sle micro
###### 5. rancher prime on suse linux
##### todo: control plane (dns server, openvpn, cert manager, ipam) setup, subnet vlan route, vlan static ips, ip manager, ansible plays to automate stack, agama to automate os installations, cloud init files, wiki for engineering and operations, service to submit support cases, cost models, monitoring, backup/recovery, high availability, separating the compute from the data plane



OPENVPN SERVER.CONFIG Template


port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh.pem
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 1.1.1.1"
keepalive 10 120
tls-auth ta.key 0
cipher AES-256-GCM
user nobody
group nobody
persist-key
persist-tun
status openvpn-status.log
verb 3
