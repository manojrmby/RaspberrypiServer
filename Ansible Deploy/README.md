# RaspberrypiServer
 Steps

# Add ssh key to Ansible host
 # ansible all -m ping -v -user pi 
# TO Verify connection
 #  ansible all -m ping -v -user pi --ask-pass
# Run
 # ansible-playbook -v main.yml --user pi --ask-pass --ask-become-pass

