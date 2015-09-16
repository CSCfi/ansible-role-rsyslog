ansible-role-rsyslog-client
=========

 - Assumes rsyslog is installed and configured to include /etc/rsyslog.d/\*.conf
 - Installs a config file into /etc/rsyslog.d 
 - Restarts rsyslog if that file changed.

Requirements
------------

Role Variables
--------------

For shipping over UDP:

central_log_host: "@Address.To.Loghost"

For shipping over TCP:

central_log_host: "@@Address.To.Loghost"


Dependencies
------------

Example Playbook
----------------

License
-------

MIT

Author Information
------------------
