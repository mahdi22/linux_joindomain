<h1>ansible-linux-join-domain</h1>
This is an ansible role to automaticaly join Linux Machine CentOS and Redhat using sssd, realm, samba and winbind. This role is tested on CentOS 7.x, 8.x and 6.6

# Requirements

- CentOS 6
- CentOS 7
- CentOS 8
- Ansible >= 2.7

# Installation

ansible-galaxy install mahdi22.ansible_linux_join_domain

# Role Variables

file: vars/main.yml
* Join_User: ADMDOMAIN # Replace ADMDOMAIN with the username domain admin
* DomainName: linuxlab.local # Replace linuxlab.local with the domainname
* Join_User_Pass: admdomainpassword # Replace admdomainpassword with the username domain admin password
* workgroup: LAB # WORKGROUP
* realm: LINUXLAB.LOCAL # Domaine Name
* server: linuxlab.local # active directory server
* kdc:
    - kerberos-1.linuxlab.local:88 # The firt Kerberos server name
    - kerberos-2.linuxlab.local:88 # The second Kerberos server name
    - kerberos-3.linuxlab.local:88 # The third Kerberos server name
* domain_realms:
    - .linuxlab.local # domaine name
    - linuxlab.local # domaine name
    
 # Example Playbook
 ```sh
- hosts: servers
  roles:
    - role: mahdi22.ansible-linux-join-domain
      become: yes
