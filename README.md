multi-project-box
=================

Deployment template for hosting multiple projects with multiple environments under the same box.
(In progress...)
[![Build Status](https://travis-ci.org/salvadormrf/multi-project-box.svg?branch=master)](https://travis-ci.org/salvadormrf/multi-project-box)  

- Get a box
- Buy a domain e.g. **zendevbox.com**
- Set a wildcard record **\*.zendevbox.com** to the box ip address
- Buy a wildcard **SSL certificate** and install on your load balancer (optional)
- Configure jenkins to auto-deploy on commits (optional)
    
##### Project will be available like:
    https://myproject-dev.zendevbox.com
    https://myproject-test.zendevbox.com
    https://myproject-stage.zendevbox.com


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


#### Drupal Project Stack
    - ubuntu
    - memcached
    - mysql
    - php5
    - php5-fpm
    - drupalapp
    - nginx
    - varnish
	
    # Includes 
        - drush clear cache
        - drush features revert
        - database import/backup | soon
	
---
#### Deployment | Examples

###### Django Project 
    # DEV environment
    ansible-playbook deployment/ansible/playbook/site_django.yml -i deployment/ansible/inventory-example-django/dev
    
###### Static Project 
    # DEV environment
    ansible-playbook deployment/ansible/playbook/site_static.yml -i deployment/ansible/inventory-example-static/dev
    
###### Drupal Project 
    # DEV environment
    ansible-playbook deployment/ansible/playbook/site_drupal.yml -i deployment/ansible/inventory-example-static/dev
	
	
# TODO
- Documentation
- Vagrant box support
- Django advanced settings
- Database backup
- Database import
- Tests
- Ansible Coding Conventions https://github.com/edx/configuration/wiki/Ansible-Coding-Conventions
