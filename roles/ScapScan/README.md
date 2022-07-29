Role Name: ScapScan
=========

This role will run an OpenSCAP scan on RHEL 7 8 and 9 systems and will generate an html report than can set to a reports server if desired

Requirements
------------

Role Variables
--------------
The available profiles for the various versions are in vars/main.yml
You should choose the appropriate profile and put it in the appropriate profile variable in defaults/main.yml
If you have customized the profile you will need to put the tailoring file in files/ and then and the tailing file name in the appropriate variable in defaults/main.yml
You will also need to examine that file for the embedded profile name - you can do this by running the command: oscap info <tailoring file>.  You will then have to put that profile name in the correct varialbe in defaults/main.yml

You can also set:
1) whether to copy the reports some where
2) the destination where the reports should be sent - using scp

Note that when you run the scap scan there will likely be some failures - with lots of red output - this is the way the oscap scan works.  We simply ignore the failure of the scan - that just means some requirements did not pass.

Dependencies
------------


Example Playbook
----------------
---
- name: use ScapScan role
  become: yes
  hosts: all

  roles:
    - ScapScan

License
-------

BSD

Author Information
------------------

Rick Ring
rring@redhat.com

with help from Will Tome, Red Hat
