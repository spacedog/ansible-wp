[![Build Status](https://travis-ci.org/spacedog/ansible-wp.svg?branch=master)](https://travis-ci.org/spacedog/ansible-wp)

Ansible Wordpress Role
=========

Manages Latest wordpress installation

Requirements
------------

Nothing particular is reuquired to run the role


Role Variables
--------------

*wp_salt_static* - sets authentication unique keys and salts.

  - wp_salt_static:
      AUTH_KEY: 'put your unique phrase here'
      SECURE_AUTH_KEY: 'put your unique phrase here'
      LOGGED_IN_KEY: 'put your unique phrase here'
      NONCE_KEY: 'put your unique phrase here'
      AUTH_SALT: 'put your unique phrase here'
      SECURE_AUTH_SALT: 'put your unique phrase here'
      LOGGED_IN_SALT: 'put your unique phrase here'
      NONCE_SALT: 'put your unique phrase here'

*wp_owner* - sets owner of WordPress files on the target server. Should match the user of web server

  - wp_owner: apache

*wp_group* - sets group of WordPress files on the target server. Should match the user of web server

  - wp_group: apache

*wp_source_dir* - sets the dir to store wordpress source files

  - wp_source_dir: /opt/source/wordpress

*wp_dest_dir* - sets the destination directory where to put wordpress

  - wp_dest_dir: /var/www/html

*wp_mysql_host* - sets the  mysql host name

  - wp_mysql_host: 'localhost'

*wp_mysql_db* - sets the db name for wordpress

  - wp_mysql_db: "wp_{{ansible_hostname}}"

*wp_mysql_user* - sets the db user for wordpress

  - wp_mysql_user: wp_admin

*wp_mysql_password* - sets the db user password for wordpress

  - wp_mysql_password: undefined

Dependencies
------------

None

Example Playbook
----------------

- name: Install WordPress
  hosts: wp
  sudo: yes
  vars:
    wp_mysql_password: somepassword
    wp_mysql_host: db_host
  roles:
    - httpd
    - mysql
    - wp

License
-------

BSD

Author Information
------------------

Anton Baranov <abaranov@linux.com>
