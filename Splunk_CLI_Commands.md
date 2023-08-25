# Splunk Administrative CLI commands

The Command Line Interface (CLI) commands can be executed from the $SPLUNK_HOME/bin directory.
Replace $SPLUNK_HOME with the actual path to your Splunk installation directory.

----------------------------------------------------------------------------------------------
__To add user:__  
./splunk add user &lt;new-usernmae&gt; -password &lt;password_for_user&gt; -role &lt;role_name&gt; -auth &lt;admin_username&gt;:&lt;admin_password&gt;

__To add license:__  
./splunk add licenses &lt;path_to_license_file_required&gt; 

__To check splunk status:__  
/splunk status

__To check the forward server details that are configured in outputs.conf:__  
./splunk list forward-server

__Shows which deployment server it is configured to poll from:__  
./splunk show deploy-poll

__Sets deployment server to poll updates from:__  
./splunk set deploy-poll &lt;DS-host:port&gt; 

__Reload you deployment server, in entirety or by serverclass:__  
./splunk reload deploy-server

__btool command:__  
./splunk btool &lt;conf_file_prefix&gt; [list|layer|add|delete] --debug --app=&lt;app_name&gt; --user=&lt;user_name&gt;

__btool check command to find typos in conf file stanzas:__  
./splunk btool check

__command to disable Web UI interface on Splunk:__  
./splunk disable webserver

__To add a standalone indexer to search head for Distributed search configuration:__  
./splunk add search-server &lt;scheme&gt;://&lt;host&gt;:&lt;port&gt; -auth &lt;user&gt;:&lt;password&gt; -remoteUsername &lt;peer-user&gt; -remotePassword &lt;peer-password&gt;

__To add non-multisite indexer cluster to search head for Distributed search:__  
./splunk add cluster-manager &lt;scheme&gt;://&lt;host&gt;:&lt;port&gt; -secret &lt;indexers-pass4symmkey&gt; -multisite false

__To quarantine and unquarantine a search peer:__  
./splunk edit search-server -auth &lt;user&gt;:&lt;password&gt; &lt;host&gt;:&lt;port&gt; -action [quarantine|unquarantine]

__To add File & Directory monitoring inputs:__  
./splunk add monitor &lt;monitor file or  directory location&gt; -index &lt;index-name&gt; -sourcetype &lt;source type value&gt; -hostname &lt;host value to set&gt;

__btprobe command to reset fishbucket for specific source:__  
./splunk cmd btprobe -d $SPLUNK_HOME/var/lib/splunk/fishbucket/splunk_private_db --file &lt;source&gt; --reset

__To reset fishbucket for all sources, must execute with caution:__  
./splunk clean eventdata index _thefishbucket
