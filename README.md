Sript to create Symfony2 local project
======================================

This work on **Ubuntu** systems 

- Automatically create virtual host
- Fill **hosts** file *if it needed*
- Create the project folder 
- Download, extract symfony
- ACL permissions to cache & logs

You need to have ACL installed and enabled. Check your fstab.

The project has this files:

- template.site: just a template for your .site vhost files
- vhostcreate :  bash script that generate vhost files form the template.site file
- hostexist: bash script to check if some host exist in your /etc/hosts file
- putacl: bash script usefull to set the correct permiss in app/cache & app/logs
- createpj: the main script that made all
- README.md: this file

The "putacl" script assumes that the apache user is 'www-data', but you can edit it.


Install
-------

Just download and unzip "astart" project.

Config
------

Copy config.dst to config

```
mv config.dst config
```

Edit the  script and configure  this vars

```
USER:   your user
MYPRJ:  your projects folders i.e: /home/$USER/projects
EXT:    domain ej: local or loc 
SERVERIP: apache ip usually 127.0.0.1 for local
SF2VERSION: Symfony version to install i.e: 2.0.4
```

*You probably don't need to change the config*

USE 
---

You want to create a new project "blog". 

```
./astart/createpj blog
```

The script will ask you about yout root pass for 'sudo' operations.
After that you will have a blog folder with symfony and a vhost called blog.local

PD: You can use others script by separate.

*generate vhost files*

```
./astart/vhostcreate projectname super_domain projects_folder 

i.e: ./astart/vhostcreate blog local /home/myuser/myprojectsfolder
```

*putacl*

from your project folder

```
./astart/putacl  or ./astart/putacl myuser myprojectfolder 
```


