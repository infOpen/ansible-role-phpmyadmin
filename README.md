phpmyadmin
==========

[![Build Status](https://travis-ci.org/infOpen/ansible-role-phpmyadmin.svg?branch=master)](https://travis-ci.org/infOpen/ansible-role-phpmyadmin)

Install phpmyadmin package.

Requirements
------------

This role requires Ansible 1.4 or higher, and platform requirements are listed
in the metadata file.

Role Variables
--------------

Default role variables

    # Defaults file for phpmyadmin

    # Package variables
    phpmyadmin_package_state : present

    # Schema management
    phpmyadmin_database_import_schema : True
    phpmyadmin_database_import_user   : "root"
    phpmyadmin_database_import_file   : "/usr/share/dbconfig-common/data/phpmyadmin/install/mysql"

    # Website management
    phpmyadmin_website_use_default_apache_conf : True
    phpmyadmin_website_apache_config_file      : "/etc/phpmyadmin/apache.conf"
    phpmyadmin_website_apache_active_link      : "/etc/apache2/sites-enabled/phpmyadmin.conf"
    phpmyadmin_website_webserver_used          : "apache"
    phpmyadmin_website_webserver_service_name  : "apache2"
    phpmyadmin_website_webserver_state         : "restarted"

    # Database server
    phpmyadmin_database_preparation: true
    phpmyadmin_db_name   : "phpmyadmin"
    phpmyadmin_db_type   : "mysql"
    phpmyadmin_db_server :
      basepath : ""
      user     : root
      password : ""
      host     : localhost
      port     : 3306

    # Database account
    phpmyadmin_db_account :
      user       : phpmyadmin
      password   : phpmyadmin
      privileges :
        - "phpmyadmin.*:ALL"


Debian specific variables :

    # Debian specific variables
    phpmyadmin_packages :
      - phpmyadmin

    phpmyadmin_dbconfig_state : present

    # dbconfig settings
    phpmyadmin_dbconfig_file       : "/etc/dbconfig-common/phpmyadmin.conf"
    phpmyadmin_dbconfig_file_owner : "root"
    phpmyadmin_dbconfig_file_group : "root"
    phpmyadmin_dbconfig_file_mode  : "0600"

    phpmyadmin_dbconfig_install : False
    phpmyadmin_dbconfig_upgrade : False
    phpmyadmin_dbconfig_remove  : ""

    phpmyadmin_dbconfig_ssl : ""
    phpmyadmin_dbconfig_authmethod_admin : ""
    phpmyadmin_dbconfig_authmethod_user  : ""


Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - { role: achaussier.apache }
        - { role: achaussier.mysql-server }
        - { role: achaussier.phpmyadmin }

License
-------

MIT

Author Information
------------------

Alexandre Chaussier (for Infopen company)
- http://www.infopen.pro
- a.chaussier [at] infopen.pro
