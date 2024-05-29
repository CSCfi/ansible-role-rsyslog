[![Build Status](https://travis-ci.org/CSCfi/ansible-role-rsyslog.svg)](https://travis-ci.org/CSCfi/ansible-role-rsyslog)
ansible-role-rsyslog
=========

 - Assumes /etc/rsyslog.conf is as distributed where it includes /etc/rsyslog.d/\*.conf
 - Installs a config file into /etc/rsyslog.d/
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
<pre>
central_log_host: "@Address.To.Loghost"
</pre>
For shipping over TCP:
<pre>
central_log_host: "@@Address.To.Loghost"
</pre>
For listening:
<pre>
 - central_log_listener: false
 - central_logs_directory: "/var/log/remote/servers"
 - central_logs_retention_days: 30
 - central_log_by_function: false
</pre>
Setting log_by_function to true will store logs not in %hostname% but per function instead.

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

There is also option to setup secondary log host for forwarding. See defauls/main.yml for params.

Dependencies
------------

Example Playbook
----------------

License
-------

MIT

Author Information
------------------
