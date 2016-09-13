Role Name
=========

Este playbook levanta un servidor samba basico, crea un rol admin, que tiene acceso a la carpeta raiz /respaldo/allaccess/, y un segundo usuario que solo tiene acceso a un subdirectorio /respaldo/allaccess/secured1.

Requirements
------------
El playbook se corrio en el siguiente ambiente:

- ansible 2.0.1.0
- ubuntu 14.04.5

Role Variables
--------------
Se utilizan las sigiuente variables:

samba_shares:
  - {'name': 'resplado', 'path':'/respaldo/allaccess/'}
  - {'name': 'secured', 'path':'/respaldo/allaccess/secured'}
  - {'name': 'secured1', 'path':'/respaldo/allaccess/secured1'}

samba_users:
  - {'name': 'admin', 'password':'123'}
  - {'name': 'admin1', 'password':'123'}

Para el archivo smb.conf, la asignacion de usuario es estatica, un usuario con acceso total y uno con solo acceso a una carpeta:

path = /respaldo/allaccess/
valid users = admin
path = /respaldo/allaccess/secured
valid users = admin
[secured1]
path = /respaldo/allaccess/secured1
valid users = admin,admin1


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

Author Information
------------------

@gio_uchiha
