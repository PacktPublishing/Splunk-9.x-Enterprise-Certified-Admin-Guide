# Splunk Administrative CLI commands

The Command Line Interface (CLI) commands can be executed from the $SPLUNK_HOME/bin directory.
Replace $SPLUNK_HOME with the actual path to your Splunk installation directory.
----------------------------------------------------------------------------------------------
To add user:
./splunk add user supportuser -password changeme2 -role supportgroup -auth admin:changeme

To add license:
splunk add licenses <path_to_license_file_required> 

To check splunk status:
/splunk status

To check the forward server details that are configured in outputs.conf:
./splunk list forward-server

Shows which deployment server it is configured to poll from:
./splunk show deploy-poll

Sets deployment server to poll updates from:
./splunk set deploy-poll <DS-host:port> 

Reload you deployment server, in entirety or by serverclass:
./splunk reload deploy-server

btool command:
./splunk btool <conf_file_prefix> [list|layer|add|delete] --debug --app=<app_name> --user=<user_name>

btool check command to find typos in conf file stanzas:
./splunk btool check

command to disable Web UI interface on Splunk:
./splunk disable webserver

To add a standalone indexer to search head for Distributed search configuration:
./splunk add search-server <scheme>://<host>:<port> -auth <user>:<password> -remoteUsername <peer-user> -remotePassword <peer-password>

To add non-multisite indexer cluster to search head for Distributed search:
./splunk add cluster-manager <scheme>://<host>:<port> -secret <indexers-pass4symmkey> -multisite false

To quarantine and unquarantine a search peer:
./splunk edit search-server -auth <user>:<password> <host>:<port> -action [quarantine|unquarantine]

To add File & Directory monitoring inputs:
./splunk add monitor <monitor file or  directory location> -index <index-name> -sourcetype <source type value> -hostname <host value to set>

btprobe command to reset fishbucket for specific source:
./splunk cmd btprobe -d $SPLUNK_HOME/var/lib/splunk/fishbucket/splunk_private_db --file <source> --reset

To reset fishbucket for all sources, must execute with caution:
./splunk clean eventdata index _thefishbucket
