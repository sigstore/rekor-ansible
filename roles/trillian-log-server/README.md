Role Name
=========

This roles installs the Trililan transparency log using Go's built in get and build actions.

Requirements
------------

This role requires a MariaDB (/MySQL) database to be installed and running, as Trillian uses a MySQL compatible database.
A script designed to prepare the user/password and database is included and used
by this role.

Role Variables
--------------

N/A

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: trillian-log-server }

License
-------

Apache 2.0

Author Information
------------------

axel simon <axel@redhat.com>
