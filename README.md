multi-project-box
=================

Deployment template for hosting multiple projects with multiple environments under the same box.
(In progress...)

---
#### Django Project Stack

    - ubuntu
    - memcached
    - nginx
    - postgres
    - mysql
    - uwsgi
    - django
    
    # Includes 
        - database migrations
        - cron jobs


#### Static Project Stack

    - ubuntu
    - nginx


#### Drupal Project Stack (soon)
    - ubuntu
    - memcached
    - mysql
    - php5
    - drupalapp
    - php5-fpm
    - nginx
    - varnish
	
---
#### Deployment | Examples

###### Django Project 
    # DEV environment
    ansible-playbook deployment/ansible/playbook/site.yml -i deployment/ansible/inventory-example-django/dev
    
###### Static Project 
    # DEV environment
    ansible-playbook deployment/ansible/playbook/staticwebservers.yml -i deployment/ansible/inventory-example-static/dev
    
###### Drupal Project 
    # DEV environment
    ...
	
# TODO
- Documentation
- Vagrant box support
- Django advanced settings
- Database backup
- Database import
- Tests
- Ansible Coding Conventions https://github.com/edx/configuration/wiki/Ansible-Coding-Conventions
