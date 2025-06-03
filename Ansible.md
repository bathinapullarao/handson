# 🤖 Ansible 

---

## 🛠️ Getting Started

### 1. Install Ansible
- On Ubuntu:
  ```bash
  sudo apt update
  sudo apt install ansible -y
2. Check Version and Configuration
Commands:

bash
Always show details

Copy
ansible --version
ansible-config list
🗂️ Inventory Management
3. Create a Static Inventory File
Sample inventory.ini:

ini
Always show details

Copy
[webservers]
web1 ansible_host=192.168.1.10

[dbservers]
db1 ansible_host=192.168.1.20
4. Use Dynamic Inventory
Write a script or use cloud inventory plugins (e.g., AWS, GCP)

📋 Ad-Hoc Commands
5. Run Ad-Hoc Commands
Ping all hosts:

bash
Always show details

Copy
ansible all -i inventory.ini -m ping
Install a package:

bash
Always show details

Copy
ansible webservers -m apt -a "name=nginx state=present" -b
📜 Playbooks
6. Write a Basic Playbook
playbook.yml:

yaml
Always show details

Copy
- hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
7. Run a Playbook
Command:

bash
Always show details

Copy
ansible-playbook -i inventory.ini playbook.yml
🔄 Loops and Conditionals
8. Use Loops in Playbooks
yaml
Always show details

Copy
- name: Create multiple users
  user:
    name: "{{ item }}"
    state: present
  loop:
    - user1
    - user2
9. Use Conditions
yaml
Always show details

Copy
- name: Only run if OS is Ubuntu
  apt:
    name: htop
    state: present
  when: ansible_distribution == "Ubuntu"
🔐 Vault and Secrets
10. Encrypt a File with Ansible Vault
bash
Always show details

Copy
ansible-vault encrypt secrets.yml
11. Use Vault in a Playbook
bash
Always show details

Copy
ansible-playbook --ask-vault-pass playbook.yml
🧩 Roles and Reuse
12. Create a Role
bash
Always show details

Copy
ansible-galaxy init myrole
13. Use Roles in a Playbook
yaml
Always show details

Copy
- hosts: all
  roles:
    - myrole
🔀 Handlers and Notifications
14. Add Handlers
yaml
Always show details

Copy
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
📦 Templates and Variables
15. Use Variables and Templates
vars.yml:

yaml
Always show details

Copy
my_port: 8080
template.conf.j2:

conf
Always show details

Copy
listen {{ my_port }}
Task:

yaml
Always show details

Copy
- name: Template config
  template:
    src: template.conf.j2
    dest: /etc/myapp/config.conf
🌐 Ansible for Cloud (AWS Example)
16. Install AWS Collection and Use EC2 Modules
bash
Always show details

Copy
ansible-galaxy collection install amazon.aws
Example Task:

yaml
Always show details

Copy
- name: Launch EC2
  amazon.aws.ec2_instance:
    name: my-instance
    instance_type: t2.micro
    image_id: ami-0abcdef1234567890
    region: us-east-1
    key_name: mykey
    count: 1
📈 Advanced Topics
17. Use Tags
yaml
Always show details

Copy
- name: Install Docker
  apt:
    name: docker.io
    state: present
  tags: docker
18. Limit Execution by Host
bash
Always show details

Copy
ansible-playbook playbook.yml --limit web1
19. Dry Run
bash
Always show details

Copy
ansible-playbook playbook.yml --check
🔍 Debugging and Logging
20. Use Debug Module
yaml
Always show details

Copy
- name: Show debug info
  debug:
    var: ansible_hostname
21. Enable Logging
In ansible.cfg:

ini
Always show details

Copy
[defaults]
log_path = ./ansible.log
🧪 Testing with Molecule (Optional)
22. Install Molecule
bash
Always show details

Copy
pip install molecule[docker]
23. Test Role
bash
Always show details

Copy
molecule init role myrole
cd myrole
molecule test
"""

Save to Markdown file
ansible_md_path = Path("/mnt/data/ansible_hands_on_tasks.md")
ansible_md_path.write_text(ansible_md_content.strip())

Return file path
ansible_md_path
