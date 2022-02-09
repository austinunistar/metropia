# Deploy Nomad & Consult via ansible, on Centos nodes on Vagrant local environment#

Vagrant ENV: Ubuntu 18.04 with latest virtualbox, vagrant, ansible installed

NOTE: vagrant plugin install vagrant-vbguest

vagrant up

Change consul (January 12, 2022) and nomad (February 1, 2022) versions to latest

$ grep version ansible-role-consul/defaults/main.yml 

consul_version: 1.11.2

consul_webui_version: 1.11.2

$ grep version ansible-role-nomad/defaults/main.yml 

nomad_version: 1.2.5

$ ansible-playbook -i ./inventory playbook.yml

for node2-3 : sudo usermod -aG docker vagrant ; exit; 
    
## Troubleshooting

check nomad status

    nomad status
    nomad node status  
    nomad server members

Examples:

[vagrant@node-2 ~]$ nomad server members
Name          Address        Port  Status  Leader  Protocol  Build  Datacenter  Region
node1.global  192.168.56.10  4648  alive   true    2         1.2.5  dc1         global
[vagrant@node-3 ~]$ nomad node status
ID        DC   Name   Class   Drain  Eligibility  Status
93fb8dca  dc1  node2  <none>  false  eligible     ready
920745c4  dc1  node3  <none>  false  eligible     ready
[vagrant@node-3 ~]$ nomad version
Nomad v1.2.5 (06d912a20ba029c7f4d6b371cd07594cba3ae3cd)
[vagrant@node-3 ~]$ consul version
Consul v1.11.2
Revision 37c7d06b
Protocol 2 spoken by default, understands 2 to 3 (agent will automatically use protocol >2 when speaking to compatible agents)