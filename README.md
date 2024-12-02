# Install VS-Code / VS-Codium

## Description
This role installs VS-Code or VS-Codium on a Linux PC.
You can install at different Systems:
  - Debian and Debian like
  - Red Hat and Red Hat like (not tested)
  - Raspberry Pi OS

## Description of the installation procedure

Entry Point task/main.yml

### 1. USER DECISION: install VS-Code or VS-Codium
  make your decision what to install

### 2. prepare extensionlist
  load the extensions from the /vars/*.extensions.yml file
  prepare it for installation
  ready to use in a Dictionary: extensions_var

  file: tasks/prepare_extensions_to_install.yml

### 3. prepare hostlist
  generates a var userlist with all users from each hosts.
  #### example:
  ~~~yml
  userlist:
    - host_name: host1
      users: ['user1_host1', 'user2_host1', 'user3_host1']
    - host_name: host2
      users: ['user1_host2', 'user2_host2']
  ~~~
  gather user from all hosts and saves in userlist
  there will will be a file in /var/userlist.yml with the userlist
  it is a workaround because i dont know how to save the users in the way i need it

  file: tasks/prepare_host_to_install.yml

### 4. get the OS-System
  get the OS-System an save it in a boolean Var

### 5. start installation 
  install VS-Code oder VS-Codium inclusive the Extensions for each user.

# Role Variables
--------------
/vars/username.extensions.yml
~~~yml
vscode_extensions_for:
  - username: username
    extensions:
      - identifier of the extension 
      - ...
~~~

# Example Playbook
----------------
~~~yml
- hosts: workstations
  roles:
     - vscode_codium
~~~
# What to do next
- at vars/user.extensions.yml
    - add user decision vs-code or vs-codium
    - change user into a list of users

- test the role on a RHEL-System

# License
-------

CC 4.0 by

# Author Information
------------------

Andreas Vonrhein.
Teacher at professional school for IT & construction technology
