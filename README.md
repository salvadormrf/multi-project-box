multi-project-box
=================

Deployment template for hosting multiple projects with multiple environments under the same box.


---
#### Boot development box
	# install required vagrant plugins
	vagrant plugin install vagrant-hostmanager
    vagrant up
    vagrant ssh
    ./myproject-local/run.sh
    
	# App: http://myprojectname.dev:8000
	# Email: http://myprojectname.dev:1080
	

#### Deployment with ansible | Examples

    # install deploy requirents (deploy-requirements.txt)
    # make sure you have ssh access to the destination servers
    mkvirtualenv myprojectname
    pip install -r deployment/deploy-requirements.txt
    
    # deploy with ansible to vagrant box
    ansible-playbook deployment/ansible/playbook/vagrant.yml -i deployment/ansible/inventory/vagrant --private-key=~/.vagrant.d/insecure_private_key
	
    # deploy with ansible to DEV
    ansible-playbook deployment/ansible/playbook/site.yml -i deployment/ansible/inventory/dev
 
    # deploy with ansible to DEV | and update only nginx
    ansible-playbook deployment/ansible/playbook/site.yml -i deployment/ansible/inventory/dev --tags=nginx


# TODO
- Documentation
- SSL support
- Vagrant box
- Django advanced settings
- Static app
- Database backup
- Database import
- Tests
- Ansible Coding Conventions https://github.com/edx/configuration/wiki/Ansible-Coding-Conventions
