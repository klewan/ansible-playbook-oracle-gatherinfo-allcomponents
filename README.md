Ansible Playbook: oracle-gatherinfo-allcomponents
=================================================

Gather information about installed Oracle components.

This is an example how to use `oracle-gatherinfo-gi`, `oracle-gatherinfo-databases`, `oracle-gatherinfo-listener` and `oracle-gatherinfo-dbconsole` roles to dynamically collect a lot of information about Oracle components installed on database servers. Information collected may be used in many other roles/playbooks for further processing or building other functionalities.

A few variables are populated:

* local `oracle_gatherinfo_gi_gi_info` (and global `oracle_gi_info`) - Grid Infrastructure details
* local `oracle_gatherinfo_databases_oracle_databases` (and global `oracle_databases`) - a list describing the databases hosted on the servers
* local `oracle_gatherinfo_listener_registered_listeners` (and global `oracle_registered_listeners`) - a list describing Oracle listeners registered in GI OHAS
* local `oracle_gatherinfo_listener_running_listeners` (and global `oracle_running_listeners`) - a list describing active/running Oracle listeners
* local `oracle_gatherinfo_dbconsole_registered_services` (and global `oracle_dbconsole_registered_services`) - a list describing db console services registered in GI OHAS
* local `oracle_gatherinfo_dbconsole_running_services` (and global `oracle_dbconsole_running_services`) - a list describing active/running db console services


Supported OS:
-------------
* RedHat
* CentOS
* OracleLinux

Requirements
------------

This playbook requires the `oracle`, `oracle-gatherinfo-gi`, `oracle-gatherinfo-databases`, `oracle-gatherinfo-listener` and `oracle-gatherinfo-dbconsole` roles.

`$ ansible-galaxy install -r roles/requirements.yml`

Examples
--------

    $ ansible-playbook playbook.yml --list-tasks
    $ ansible-playbook playbook.yml --list-tags

Collect all data (GI, databases, dbconsole services)

    $ ansible-playbook playbook.yml

Collect data about Grid Infrastructure

    $ ansible-playbook playbook.yml --tags=oracle-gatherinfo-gi
	
Collect data about Grid Infrastructure along with GI patches and ASM diskgroups 

    $ ansible-playbook playbook.yml --tags=oracle-gatherinfo-gi --extra-vars='{oracle_gatherinfo_gi_get_grid_home_patches: true, oracle_gatherinfo_gi_get_extra_facts: true}'

Collect data about Oracle databases registered in the GI registry

    $ ansible-playbook playbook.yml --tags=oracle-gatherinfo-gi,oracle-gatherinfo-databases

Collect data about Oracle databases registered in the GI registry along with DB patches

    $ ansible-playbook playbook.yml --tags=oracle-gatherinfo-gi,oracle-gatherinfo-databases --extra-vars='{oracle_gatherinfo_databases_get_oracle_home_patches: true}'

Collect data about Oracle Listeners

    $ ansible-playbook playbook.yml --tags=oracle-gatherinfo-gi,oracle-gatherinfo-listener

Collect data about Database Console services

    $ ansible-playbook playbook.yml --tags=oracle-gatherinfo-gi,oracle-gatherinfo-dbconsole

	
License
-------

GPLv3 - GNU General Public License v3.0

Author Information
------------------

This playbook was created in 2018 by [Krzysztof Lewandowski](mailto:Krzysztof.Lewandowski@fastmail.fm).


