Create/Update/Delete Resource Group in Azure
=========

Use this role to create, update, delete a resource group in Azure

Requirements
------------

ansible >=2.7.0
Requires Azure_rm Modules

[Azure Account information]('https://docs.ansible.com/ansible/latest/scenario_guides/guide_azure.html')
[Azure Resource module options]('https://docs.ansible.com/ansible/latest/modules/azure_rm_resourcegroup_module.html')

Role Variables
--------------

```yaml
resource_group: #The name you want to call your RG group
location: #the azure location of the RG
rg_state: #Use this variable to define state absent to remove the resource group
```

>Note, this role will not delete a resource group that has objects in it. That function can be added

Dependencies
------------

None

Example Playbook
----------------

> Create a new Resource Group

```yaml
- name: Azure Playbook for a single Azure Resource Group
  hosts: localhost
  pre_tasks:
    - name: Setting desired state
      set_fact:
#dependency Vars
        resource_group: test
        location: canadacentral

  connection: local

  roles:
    - azure-resourcegroup
```

> Deleting an existing Resource Group

```yaml
- name: Azure Playbook for a single Azure Resource Group
  hosts: localhost
  pre_tasks:
    - name: Setting desired state
      set_fact:
#dependency Vars
        resource_group: test
        rg_state: absent

  connection: local

  roles:
    - azure-resourcegroup
```

License
-------

MIT

Author Information
------------------

Adam Brassard: Abrass on IRC
