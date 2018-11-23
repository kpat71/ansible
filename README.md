# Ansible for dummies

# Best practise document
https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html


# Userdata for runnin ansible 
cd /tmp
# install PIP
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
# Install ansible
pip install 'ansible==2.7.2'
# Install GIT client
yum install -y git
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