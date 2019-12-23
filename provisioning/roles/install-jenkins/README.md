Role Name
=========

Installs jenkins by downloading jenkins.war

Requirements
------------

Java

Role Variables
--------------

download_url --> URL of jenkins.war
jenkins_war --> destination path of downloaded jenkins.war

Dependencies
------------

install-openjdk or install-oracle-java roles needed to be installed.
Jenkins supports JDK8 and JDK11. It is advised to use with JAVA8.
For further info, have a look at https://jenkins.io/doc/administration/requirements/java/


Example Playbook
----------------

- name: Install Jenkins
  roles:
    - install-openjdk
    - install-jenkins

	
License
-------

BSD

Author Information
------------------

Sevket Kursad KAHYA
sevketkkahya@gmail.com