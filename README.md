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