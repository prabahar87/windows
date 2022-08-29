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

# Dot-Net-Installation

## How to run the Dot-Net-Installation role.

```
ansible-playbook Dot-Net-Installation.yml
or
ansible-playbook Dot-Net-Installation.yml -vvv <<Verbose Mode>>
```

## Varibale Name
It's under the Dot-Net-Installation role and u can find the vars folder over here.

| Variable | Variable_Values |
| ------ | ------ |
| Win_DotNet_Path | HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full |
| Win_DotNet_Name | .NET Framework 4.7 |


## Dot-Net-Installation.yml
```
---
- hosts: win << Define the HostGroup Name Here >>
  gather_facts: true << It should be true only. Because we used ansible facts inside the playbook >>
  roles:
      - Dot-Net-Installation
```

## Test Results
```
ansible-playbook dotnet.yml

PLAY [win] ********************************************************************************************************************************************************************

TASK [Gathering Facts] ********************************************************************************************************************************************************
ok: [192.168.1.102]

TASK [Check .NET version.] ****************************************************************************************************************************************************
ok: [192.168.1.102]

TASK [Validate if the computer is having Dot Net FrameWork or not.] ***********************************************************************************************************
ok: [192.168.1.102] => {
    "msg": "Dot Net Framework Already Installed on this machine. V4 is available on here. \n"
}

TASK [Install .Net 3.5] *******************************************************************************************************************************************************
skipping: [192.168.1.102]

TASK [Check .NET version.] ****************************************************************************************************************************************************
ok: [192.168.1.102]

TASK [Validate if the computer is having Dot Net FrameWork or not.] ***********************************************************************************************************
ok: [192.168.1.102] => {
    "msg": "We have successfully installed the Dot Net FrameWork. \n"
}

PLAY RECAP ********************************************************************************************************************************************************************
192.168.1.102              : ok=5    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0 
```