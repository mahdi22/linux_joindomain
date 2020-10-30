<h1>ansible-linux-join-domain</h1>
This is an ansible role to automaticaly join Linux Machine CentOS and Redhat using sssd, realm, samba and winbind. This role is tested on RedHat/CentOS 7.x, 8.x 6.6 and Ubuntu 20 18 16 and Debian 10 9

# Requirements

- source.list configured and updated for debian servers
- Ansible >= 2.7

# Installation

ansible-galaxy install mahdi22.linux_joindomain

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
    - role: mahdi22.linux_joindomain
      become: yes
