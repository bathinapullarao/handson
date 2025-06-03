# 🤖 Ansible 

---

## 🛠️ Getting Started

### 1. Install Ansible
- On Ubuntu:
  ```
  sudo apt update
  sudo apt install ansible -y
  ```
2. Check Version and Configuration
```
ansible --version
ansible-config list
```

🗂️ Inventory Management
4. Create a Static Inventory File  
Sample inventory.ini:  
```
[webservers]
web1 ansible_host=192.168.1.10

[dbservers]
db1 ansible_host=192.168.1.20
```
4. Use Dynamic Inventory  
Write a script or use cloud inventory plugins (e.g., AWS, GCP)  


📋 Ad-Hoc Commands
5. Run Ad-Hoc Commands
```
Ping all hosts:
ansible all -i inventory.ini -m ping
Install a package:
ansible webservers -m apt -a "name=nginx state=present" -b
```
📜 Playbooks  
6. Write a Basic Playbook
playbook.yml:
```
- hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
```
7. Run a Playbook  
ansible-playbook -i inventory.ini playbook.yml

🔄 Loops and Conditionals  
9. Use Loops in Playbooks  
```
Copy
- name: Create multiple users
  user:
    name: "{{ item }}"
    state: present
  loop:
    - user1
    - user2
```
9. Use Conditions
```
- name: Only run if OS is Ubuntu
  apt:
    name: htop
    state: present
  when: ansible_distribution == "Ubuntu"
```


🔐 Vault and Secrets  
10. Encrypt a File with Ansible Vault  
ansible-vault encrypt secrets.yml  
11. Use Vault in a Playbook  
ansible-playbook --ask-vault-pass playbook.yml  


🧩 Roles and Reuse
12. Create a Role  
ansible-galaxy init myrole  


13. Use Roles in a Playbook
```
- hosts: all
  roles:
    - myrole
```  
🔀 Handlers and Notifications
14. Add Handlers
```
tasks:
  - name: Install Apache
    apt:
      name: apache2
      state: present
    notify: restart apache

handlers:
  - name: restart apache
    service:
      name: apache2
      state: restarted
```
📦 Templates and Variables  
15. Use Variables and Templates  
vars.yml:  
```
my_port: 8080
```
template.conf.j2:  
```
listen {{ my_port }}

Task:
Copy
- name: Template config
  template:
    src: template.conf.j2
    dest: /etc/myapp/config.conf
```
🌐 Ansible for Cloud (AWS Example)  
16. Install AWS Collection and Use EC2 Modules  
ansible-galaxy collection install amazon.aws
Example Task:
```
- name: Launch EC2
  amazon.aws.ec2_instance:
    name: my-instance
    instance_type: t2.micro
    image_id: ami-0abcdef1234567890
    region: us-east-1
    key_name: mykey
    count: 1
```
📈 Advanced Topics  
17. Use Tags
```
- name: Install Docker
  apt:
    name: docker.io
    state: present
  tags: docker
```
18. Limit Execution by Host  
ansible-playbook playbook.yml --limit web1
19. Dry Run
```
ansible-playbook playbook.yml --check  
```
🔍 Debugging and Logging
21. Use Debug Module
```
- name: Show debug info
  debug:
    var: ansible_hostname
```
21. Enable Logging  
In ansible.cfg:
```
[defaults]
log_path = ./ansible.log
```
🧪 Testing with Molecule (Optional)  
23. Install Molecule  
pip install molecule[docker]  
23. Test Role  
```
molecule init role myrole
cd myrole
molecule test
"""

Save to Markdown file
ansible_md_path = Path("/mnt/data/ansible_hands_on_tasks.md")
ansible_md_path.write_text(ansible_md_content.strip())

Return file path
ansible_md_path
```
