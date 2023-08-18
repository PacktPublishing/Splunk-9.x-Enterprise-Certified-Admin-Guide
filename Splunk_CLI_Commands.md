# Splunk Administrative CLI commands

The Command Line Interface (CLI) commands can be executed from the $SPLUNK_HOME/bin directory.
Replace $SPLUNK_HOME with the actual path to your Splunk installation directory.

----------------------------------------------------------------------------------------------
__To add user:__  
./splunk add user supportuser -password changeme2 -role supportgroup -auth admin:changeme

__To add license:__  
splunk add licenses <path_to_license_file_required> 

__To check splunk status:__  
/splunk status

__To check the forward server details that are configured in outputs.conf:__  
./splunk list forward-server

__Shows which deployment server it is configured to poll from:__  
./splunk show deploy-poll

__Sets deployment server to poll updates from:__  
./splunk set deploy-poll <DS-host:port> 

__Reload you deployment server, in entirety or by serverclass:__  
./splunk reload deploy-server

__btool command:__  
./splunk btool <conf_file_prefix> [list|layer|add|delete] --debug --app=<app_name> --user=<user_name>

__btool check command to find typos in conf file stanzas:__  
./splunk btool check

__command to disable Web UI interface on Splunk:__  
./splunk disable webserver

__To add a standalone indexer to search head for Distributed search configuration:__  
./splunk add search-server <scheme>://<host>:<port> -auth <user>:<password> -remoteUsername <peer-user> -remotePassword <peer-password>

__To add non-multisite indexer cluster to search head for Distributed search:__  
./splunk add cluster-manager <scheme>://<host>:<port> -secret <indexers-pass4symmkey> -multisite false

__To quarantine and unquarantine a search peer:__  
./splunk edit search-server -auth <user>:<password> <host>:<port> -action [quarantine|unquarantine]

__To add File & Directory monitoring inputs:__  
./splunk add monitor <monitor file or  directory location> -index <index-name> -sourcetype <source type value> -hostname <host value to set>

__btprobe command to reset fishbucket for specific source:__  
./splunk cmd btprobe -d $SPLUNK_HOME/var/lib/splunk/fishbucket/splunk_private_db --file <source> --reset

__To reset fishbucket for all sources, must execute with caution:__  
./splunk clean eventdata index _thefishbucket
