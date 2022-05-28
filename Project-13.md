# ANSIBLE-DYNAMIC-ASSIGNMENTS-AND-COMMUNITY-ROLES

## Introducing Dynamic Assignment Into Ansible Structure

Switch into a new branch(dynamuc-assignments) in your ansible-configuration 

![](images/1.png)

Create a folder Dynamic Assignments and add a file env-vars.yml 

Create a folder env-vars to keep each environment’s variables file 

![](images/2.png)

Add below configuration to env-vars.yml

![](images/3.png)

Add dynamic-assignments into the ansible playbook(sites.yml) 

![](images/4.png)

## Using Community Roles

Download MYSQL ansible roles(geerlingguy.mysq) 

`ansible-galaxy install geerlingguy.mysql`

![](images/5.png)

Configure the MYSQL role using the documentation provided to use correct credentials for MySQL required for the tooling website

![](images/6.png)

Install both Apache and Nginx community roles to use as loadbalancers

`ansible-galaxy install geerlingguy.apache`

`ansible-galaxy install geerlingguy.nginx`

![](images/7.png)

To use apache and nginx loadbalancers dynamically, declare the below variables in their configuration

Configure Apache role to serve as a loadbalncer

![](images/apachede.png)

configure Nginx role to serve as a loadbalancer

Update Nginx upstream configuration in default/main.yml and overide configuration templates

![](images/nginxdefaults1.png)

![](images/nginxtemplates.png)

Add variables to Nginx defaults/main.yml

![](images/nginxdefaults2.png)

In static-assignments folder, create lb.yml file and add the below configuration to use the loadbalancers dynamically

![](images/lb.yml.png)

In static-assignments folder, create db.yml and add below configuration for the mysql role

![](images/db-yml.png)

Update playbooks file with dyanmic assignments and loadbalancer assignments

![](images/siteplaybook.png)

Create two redhat instances to serve as UAT-webservers to deploy tooling site on

Add webserver ip addresses to inventory file  

![](images/uatyml.png)

Activate Apache loadbalancer

![](images/apacheenvars.png)

Run ansible playbook

`ansible-playbook -i inventory/uat.yml playbook/sites.yml`

![](images/apacheplay1.png)

![](images/apacheplay2.png)

![](images/apacheplay3.png)

![](images/apacheplay4.png)


Activate Nginx loadbalancer

![](images/nginxenvars.png)

Run ansible playbbok

![](images/nginxplay1.png)

![](images/nginxplay2.png)

![](images/nginxplay3.png)

![](images/nginxplay4.png)

