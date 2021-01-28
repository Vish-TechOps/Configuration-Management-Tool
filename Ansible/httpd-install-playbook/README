vs_node1@devops-tools-vm:~/devops-tools/ansible$ ls -lrt
total 16
-r-------- 1 vs_node1 vs_node1 1678 Jan 28 15:37 vs-node1-key.pem
-rw-rw-r-- 1 vs_node1 vs_node1  296 Jan 28 15:52 paybook1.yaml
-rw-rw-r-- 1 vs_node1 vs_node1  270 Jan 28 15:55 inventory.cfg

vs_node1@devops-tools-vm:~/devops-tools/ansible$ cat inventory.cfg
[servers]
#server1 ansible_host=35.223.29.148 ansible_user=vs_node1
server1 ansible_host=52.205.25.241 ansible_user=ec2-user ansible_ssh_private_key_file=/home/vs_node1/devops-tools/ansible/vs-node1-key.pem

#[all:vars]
#ansible_python_interpreter=/usr/bin/python
vs_node1@devops-tools-vm:~/devops-tools/ansible$ 
vs_node1@devops-tools-vm:~/devops-tools/ansible$ cat paybook1.yaml
-
  name: play 1
  hosts: server1
  tasks:
    - name: Execute a unix command
      command: uname -a
    - name: Install web packaage
      yum:
        name: httpd
        state: present
    - name: Start web server
      service:
        name: httpd
        state: started

vs_node1@devops-tools-vm:~/devops-tools/ansible$ ansible-playbook -i inventory.cfg paybook1.yaml -b

PLAY [play 1] *****************************************************************************************************************************************************************************************

TASK [Gathering Facts] ********************************************************************************************************************************************************************************
ok: [server1]

TASK [Execute a unix command] *************************************************************************************************************************************************************************
changed: [server1]

TASK [Install web packaage] ***************************************************************************************************************************************************************************
changed: [server1]

TASK [Start web server] *******************************************************************************************************************************************************************************
changed: [server1]

PLAY RECAP ********************************************************************************************************************************************************************************************
server1                    : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
