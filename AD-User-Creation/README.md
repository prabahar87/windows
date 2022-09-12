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


# AD-User-Creation

## How to run the AD-User-Creation role.

```
ansible-playbook AD-User-Creation.yml
or
ansible-playbook AD-User-Creation.yml -vvv <<Verbose Mode>>
```

## Varibale Name
It's under the AD-User-Creation role and u can find the vars folder over here.

| Variable | Variable_Values |
| ------ | ------ |
| Win_Package_Name| RSAT-AD-PowerShell |
| Win_State| present|
| Win_Shell_Module_Command | Get-Module |
| Win_Shell_Module_Name | ActiveDirectory |
| Win_User| << Username >> |
| Win_Domain_Path | << Domain Path >> |
| Win_Pass| << Password For User Name >> |
| Win_Domain_User | << Athuorised User Name >> |
| Win_Domain_Pass | << Athuorised User Password >> |

## ActiveDirectory.yml
```
---
- hosts: win << Define the HostGroup Name Here >>
  gather_facts: true << It should be true only. Because we used ansible facts inside the playbook >>
  roles:
      - AD-User-Creation
```


## Test Results
```
prabhu@ubuntu:~/git/windows_freelance/windows$ ansible-playbook AD-User-Creation.yml

PLAY [win] ********************************************************************************************************************************************************************

TASK [Gathering Facts] ********************************************************************************************************************************************************
ok: [192.168.1.102]

TASK [AD-User-Creation : Validate if the computer is part of domain or workgroup.] ********************************************************************************************
ok: [192.168.1.102] => {
    "msg": "      This machine joined in - \"WORKGROUP\"\n"
}

TASK [AD-User-Creation : Validate the Local user account existence.] **********************************************************************************************************
ok: [192.168.1.102]

TASK [AD-User-Creation : Validate the Domain user account existence.] *********************************************************************************************************
skipping: [192.168.1.102]

TASK [AD-User-Creation : Error Handler for Failure/Success event - queried user do not exist.] ********************************************************************************
ok: [192.168.1.102] => {
    "msg": "User do not exist. Creating the user account..!\n"
}

TASK [AD-User-Creation : Validate the Domain user account existence.] *********************************************************************************************************
skipping: [192.168.1.102]

TASK [AD-User-Creation : setfact] *********************************************************************************************************************************************
ok: [192.168.1.102]

TASK [AD-User-Creation : Creating the Domain User Account.] *******************************************************************************************************************
skipping: [192.168.1.102]

TASK [AD-User-Creation : Creating the Local User Account.] ********************************************************************************************************************
ok: [192.168.1.102]

TASK [AD-User-Creation : Validate the Local user account existence.] **********************************************************************************************************
skipping: [192.168.1.102]

TASK [AD-User-Creation : Validate the Domain user account existence.] *********************************************************************************************************
skipping: [192.168.1.102]

TASK [AD-User-Creation : Error Handler for Failure/Success event - queried user do not exist.] ********************************************************************************
ok: [192.168.1.102] => {
    "msg": "User is created successfully...!\n"
}

PLAY RECAP ********************************************************************************************************************************************************************
192.168.1.102              : ok=7    changed=0    unreachable=0    failed=0    skipped=5    rescued=0    ignored=0 

```
