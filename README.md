ansible-role-rsyslog
=========

 - Assumes rsyslog is installed and configured to include /etc/rsyslog.d/\*.conf
 - Installs a config file into /etc/rsyslog.d 
 - Restarts rsyslog if that file changed.

 - If listener is set true then setup UDP and TCP listeners on port 514
 - Create a directory to store logs
 - Configure logrotate to rotate the logs

Requirements
------------

Role Variables
--------------

For shipping over UDP:

central_log_host: "@Address.To.Loghost"

For shipping over TCP:

central_log_host: "@@Address.To.Loghost"

For listening:

 - central_log_listener: False
 - central_logs_directory: "/var/log/remote/servers"
 - central_logs_retention_days: 30

Dependencies
------------

Example Playbook
----------------

License
-------

MIT

Author Information
------------------
