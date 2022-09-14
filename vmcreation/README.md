Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).



# VM Creation/Provisioning 

## How to run the vmcreation role.

```
ansible-playbook vmcreation.yml
or
ansible-playbook vmcreation.yml -vvv <<Verbose Mode>>
```

## vmcreation.yml
```
---
- hosts: win << Define the HostGroup Name Here >>
  gather_facts: true << It should be true only. Because we used ansible facts inside the playbook >>
  roles:
      - vmcreation
```
## IIS-Installation Variable

| Variable | Variable_Values |
| ------ | ------ |
| VCenter_Name | << VCenter_Name >> |
| Vshere_user | << Vshere_user >> |
| vsphere_password | << vsphere_password >> |
| Datacenter_Name | << Datacenter_Name >> |
| Cluster_Name | << Cluster_Name >> |
| VM_Creation_Name | << VM_Creation_Name >> |
| VM_Template_Name | << VM_Template_Name >> |
| VCenter_Resource_pool_name | << VCenter_Resource_pool_name >> |

