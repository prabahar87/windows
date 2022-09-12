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


# IIS-Install

## How to run the IIS-Install role.

```
ansible-playbook IIS-Install.yml
or
ansible-playbook IIS-Install.yml -vvv <<Verbose Mode>>
```

## IIS-Install.yml
```
---
- hosts: win << Define the HostGroup Name Here >>
  gather_facts: true << It should be true only. Because we used ansible facts inside the playbook >>
  roles:
      - IIS-Install
```

| Variable | Variable_Values |
| ------ | ------ |
| website_name| example |
| website_port| 80 |
| app_pool_name | example |
| website_physicalpath | C:\\example\\com |
| website_logpath| C:\\example\\logs |
| application_name | example |
| virtual_physical_path | C:\\example\\ |
| app_physical_path | C:\\example |
| app_name | example |
| certificate | << certificate >> |
| certificate_path | << certificate_path >> |
| certificate_file_type | << certificate_file_type >> |
| certificate_password | << certificate_password >> |
| certificate_store_name | << certificate_store_name >> |


## Test Results
```
rabhu@ubuntu:~/git/windows_freelance/windows$ ansible-playbook IIS-Install.yml

PLAY [win] ********************************************************************************************************************************************************************

TASK [Gathering Facts] ********************************************************************************************************************************************************
ok: [192.168.1.102]

TASK [IIS-Install : Check if IIS service is configured.] **********************************************************************************************************************
ok: [192.168.1.102]

TASK [IIS-Install : Error Handler Success/Failure Event for IIS-Service.] *****************************************************************************************************
ok: [192.168.1.102] => {
    "msg": "IIS-Service already exists..!\n"
}

TASK [IIS-Install : Install IIS feature and management tools.] ****************************************************************************************************************
ok: [192.168.1.102]

TASK [IIS-Install : Error Handler Success/Failure Event for IIS installation.] ************************************************************************************************
ok: [192.168.1.102] => {
    "msg": "IIS is succeessfully installed..!\n"
}

TASK [IIS-Install : IIS site Configuration] ***********************************************************************************************************************************
ok: [192.168.1.102]

TASK [IIS-Install : Create an application pool] *******************************************************************************************************************************
ok: [192.168.1.102]

TASK [IIS-Install : Create webapplication on IIS.] ****************************************************************************************************************************
ok: [192.168.1.102]

TASK [IIS-Install : Create a virtual directory on an application if it does not exist] ****************************************************************************************
ok: [192.168.1.102]

PLAY RECAP ********************************************************************************************************************************************************************
192.168.1.102              : ok=9    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
