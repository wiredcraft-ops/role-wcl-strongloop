Strongloop
==========

Install strongloop and its service strong-pm.
Based on https://strongloop.com/

Requirements
------------

Need a valid node.js setup. Either Stouts.nodejs or role-wcl-nodejs

To use:

variables:

* `strongloop_install`: if setting up strongloop and strong-pm
* `strongloop_instances`: a list of config for each strongloop instance

Note:

For each config, `update` means if deploy this instance at this run.

```
---
- hosts: app
  vars_prompt:
    - name: prompt_update_1
      prompt: "Deploy this repo?"
      default: yes
      private: false
  roles:
    - role: wcl-strongloop
      strongloop_install: false
      strongloop_instances:
        - id: 1
          name: project
          update: "{{ prompt_update_1 }}"
          repo: git@github.com/someone/some_repo.git
          version: master
          env:
            NODE_ENV: production
```
