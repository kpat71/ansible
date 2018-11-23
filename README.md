# Ansible for dummies

# Git repos
git clone https://github.com/kpat71/simple_aws.git
git clone https://github.com/kpat71/ansible.git

# Best practise document
https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html


### User data part to run ansible
# Update
if [ -f '/etc/redhat-release' ]; then yum update -y; fi
if [ -f '/etc/debian_version' ]; then export DEBIAN_FRONTEND=noninteractive; fi 
if [ -f '/etc/debian_version' ]; then apt-get update && apt-get upgrade -y; fi
if [ -f '/etc/debian_version' ]; then apt-get install python -y; fi 
cd /tmp
# install PIP
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
# Install ansible
if [ -f '/etc/debian_version' ]; then pip install 'cryptography==2.4.2'; fi
pip install 'ansible==2.7.2'
# Install GIT client
if [ -f '/etc/debian_version' ]; then apt-get install -y git; fi
if [ -f '/etc/redhat-release' ]; then yum install -y git; fi
# Add github key to known hosts
ssh-keyscan -H github.com >> ~/.ssh/known_hosts
# Remove existing ansible installation 
rm -rf /tmp/ansible
# Get Ansible files from github
git clone https://github.com/kpat71/ansible.git
cd /tmp/ansible
# Make log file for ansible logs
mkdir -p /var/log/ansible/
# Add variable to put log files to log file
export ANSIBLE_LOG_PATH=/var/log/ansible/ansible.log
#  RUN ansible playbook 
ansible-playbook -i inventories/test/hosts site.yml


# Get facts from instance locally 
ansible -m setup localhost