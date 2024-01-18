# remote-server-port-test

This playbook connects to all servers defined in the inventory file and performs a port connectivity test from these servers to target servers

> How to run playbooks
```
ansible-playbook remote-server-port-test.yml -u ssh_username
```

>[!NOTE]

>If you receive a 'Timeout when waiting' error, it means there is no access

>If you receive a 'ok: [10.20.30.2] => (item=80)', it means you have access


> Outputs

```
#ansible-playbook remote-port-test.yml -u ssh_user -kK
SSH password: 
BECOME password[defaults to SSH password]: 

PLAY [Remote Server Application Port Test] **************************************************************************************************************************************************************

TASK [Monitoring Server IP] *****************************************************************************************************************************************************************************
failed: [10.20.30.1] (item=1510) => changed=false 
  ansible_facts:
    discovered_interpreter_python: /usr/libexec/platform-python
  ansible_loop_var: item
  elapsed: 4
  item: 1510
  msg: Timeout when waiting for 10.10.10.1:1510
failed: [10.20.30.3] (item=1510) => changed=false 
  ansible_facts:
    discovered_interpreter_python: /usr/libexec/platform-python
  ansible_loop_var: item
  elapsed: 4
  item: 1510
  msg: Timeout when waiting for 10.10.10.1:1510
failed: [10.20.30.2] (item=1510) => changed=false 
  ansible_facts:
    discovered_interpreter_python: /usr/libexec/platform-python
  ansible_loop_var: item
  elapsed: 4
  item: 1510
  msg: Timeout when waiting for 10.10.10.1:1510
failed: [10.20.30.2] (item=1511) => changed=false 
  ansible_loop_var: item
  elapsed: 4
  item: 1511
  msg: Timeout when waiting for 10.10.10.1:1511
...ignoring
failed: [10.20.30.1] (item=1511) => changed=false 
  ansible_loop_var: item
  elapsed: 4
  item: 1511
  msg: Timeout when waiting for 10.10.10.1:1511
...ignoring
failed: [10.20.30.3] (item=1511) => changed=false 
  ansible_loop_var: item
  elapsed: 4
  item: 1511
  msg: Timeout when waiting for 10.10.10.1:1511
...ignoring

TASK [Web Server Port Connection Test] ******************************************************************************************************************************************************************
ok: [10.20.30.2] => (item=80)
ok: [10.20.30.1] => (item=80)
ok: [10.20.30.3] => (item=80)
ok: [10.20.30.2] => (item=443)
ok: [10.20.30.1] => (item=443)
ok: [10.20.30.3] => (item=443)

TASK [Rsyslog Port Connection Test] *********************************************************************************************************************************************************************
ok: [10.20.30.2] => (item=514)
ok: [10.20.30.1] => (item=514)
failed: [10.20.30.3] (item=514) => changed=false 
  ansible_loop_var: item
  elapsed: 4
  item: 514
  msg: Timeout when waiting for 10.10.10.2:514
...ignoring

PLAY RECAP **********************************************************************************************************************************************************************************************
10.20.30.1               : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=1   
10.20.30.2               : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=1   
10.20.30.3              : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=2  
```
