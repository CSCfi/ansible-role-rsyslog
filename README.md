[![Build Status](https://travis-ci.org/CSC-IT-Center-for-Science/ansible-role-rsyslog.svg)](https://travis-ci.org/CSC-IT-Center-for-Science/ansible-role-rsyslog)
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

The listener conditional syntax is rsyslog7 specific. It uses "stop" instead of &~

It is possible to install rsyslog7 on EL6, but it's not there by default.

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
 - central_log_by_function: False

Setting log_by_function to True will store logs not in %hostname% but per function instead.

For extra settings:
<pre>
central_log_extra_settings:
 - "$MainMsgQueueType LinkedList"
 - "$MainMsgQueueHighWatermark 400000"
 - "$MainMsgQueueHighWatermark 100000"
 - "$MainMsgQueueDequeueBatchSize 10000"
 - "$MainMsgQueueSaveOnShutdown on"
 - "$MainMsgQueueWorkerThreads 8"
 - "$ActionQueueWorkerThreads 8"
 - "$ActionQueueSize 1000000"
 - "$ActionQueueDequeueBatchSize 500000"
 - "$ActionQueueType LinkedList"
</pre>

Dependencies
------------

Example Playbook
----------------

License
-------

MIT

Author Information
------------------
