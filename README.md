# ipcsd
IP Change Survey Daemon (student project)
IPCSD - IP Change Survey Daemon 
README

Overview
~~~~~~~~

	This small perl script will test a network interface
	to detect an IP change, then runs defined commands or scripts
	i.e. to change the firewall forward, etc.

	 It may be useful on a NAT behind a connection with 
	 a dynamic IP.

Requirements 
~~~~~~~~~~~~

	A GNU/Linux system with perl, ifconfig and sleep

Where can I find it ?
~~~~~~~~~~~~~~~~~~~~

	On my personnal web server at http://arachne.frgentoo.net and perhaps in 
	the future at savannah.

Install
~~~~~~~

	Download this file from http://arachne.frgentoo.net 
	to your /usr/local/bin directory. 

	Generate the default config file by typing

		# ./ipcsd -g

	Modify the config file

		# emacs /etc/ipcsd.conf

	Then run it with

		# ./ipcsd &

	 More informations : 

		# ./ipcsd --help

Usage
~~~~~

	ipcsd can be use both with command line arguments and config file.
	Use ipcsd -g to generate a default config file.

	ipcsd  [-c <path>] [-C <path>] [-d <s|r|c>] [-e <delay>] [-f <path>] 
	[-g] [-G <path>] [-h ] [-i <interface>] [-I <delay>] [-l <delay>] 
	[-m <c|r|m>] [-o <pattern>] [-p <command>] [-P <command>] 
	[-r <pattern>] [-R <command>] [-s <path>] [-t <path>] [-T <pattern>] 
	[-v] [-V]

Command line options 
~~~~~~~~~~~~~~~~~~~~

       -c | --config-file <path> : use this file instead of /etc/ipcsd.conf
       -C | --path-to-ifconfig <path> : specify the path to ifconfig
       -d | --if-down <s|r|c> : specify the action when the interface is down
                       s : stop ipcsd
                       r : reconnect interface with the reconnect-command (-R)
                       c : continue
       -e | --reconnect-interval <delay> : time to wait after reconnect
       -f | --target-file <path> : file to modify when IP changes
       -g | --generate-config-file : generate a default config file in
                       /etc/ipcsd.conf
       -G | --generate-config-file-here <path> : generate a default config file
                       at <path>
       -h | --help : print this help
       -i | --interface <interface> : survey this interface
       -I | --interval <delay> : wait <delay> seconds between each ifconfig
       -l | --long-interval <delay> : wait <delay seconds> after an IP change
       -m | --change-mode <c|r|m> : set the change mode of target file
                       c : Create new target file with template and replace
                           replace-pattern by new IP
                       r : Replace all occurence of the old IP in target file
                           the new IP
                       m : Modify target file by replacing replace-pattern by
                           the new IP
       -o | --ifconfig-output-pattern <pattern> : pattern which permit to get
                       the IP adress in the second line of an ifconfig ouput
       -p | --pre-change-command <command> : command to execute before changing
                       the target file.
       -P | --post-change-command <command> : command to execute after changing
                       the target file.
       -r | --replace-pattern <pattern> : Pattern to be replaced in the template
                       or the target file
       -R | --reconnect-command <command> : command to execute when the
                        interface is down
       -s | --path-to-sleep <path> : specify the path to sleep
       -t | --tmp-file <path> : temporary file to use insted of /tmp/ipcsd
       -T | --template <pattern> : template used to create the target file in 
                       create mode
       -v | --verbose : set the verbose mode, useful to debug
       -V | --version : print the version of ipcsd

Config file parameters 
~~~~~~~~~~~~~~~~~~~~~~

       CHANGE_MODE=""
             set the change mode of target file
               c : Create new target file with template and replace
                   replace-pattern by new IP
               r : Replace all occurences of the old IP in target file by the 
                   new IP
               m : Modify target file by replacing replace-pattern by the new IP
       IF_DOWN=""
             specify the action when the interface is down
               s : stop ipcsd
               r : reconnect interface with the reconnect-command (-R)
               c : continue
       IFCONFIG_OUTPUT_PATTERN=""
             pattern which permit to get the IP adress in the second line of an
             ifconfig ouput
       INTERFACE=""
             survey this interface
       INTERVAL=""
             wait this delay between each ifconfig
       LONG_INTERVAL=""
             wait this delay after an IP change
       PATH_TO_IFCONFIG=""
             specify the path to ifconfig
       PATH_TO_SLEEP=""
             specify the path to sleep
       PRE_CHANGE_COMMAND=""
             command to execute before changing the target file
       POST_CHANGE_COMMAND=""
             command to execute after changing the target file
       RECONNECT_COMMAND=""
             command to execute when the interface is down
       RECONNECT_INTERVAL=""
             command to execute when the interface is down
       REPLACE_PATTERN=""
             pattern to be replaced in the template or the target file
       TARGET_FILE=""
             file to modify when IP changes
       TEMPLATE=""
             template used to create the target file in create mode
       TMP_FILE=""
             temporary file to use insted of /tmp/ipcsd

Known bugs
~~~~~~~~~~

	- failure while copying TARGET_FILE on TMP_FILE in modify and replace 
	  mode, caused by unability to write TMP_FILE. Why ?

	Thank you to send your bug reports at arachne@frgentoo.net.

Author
~~~~~~

	Guillaume Morin <arachne@frgentoo.net>

Greetings
~~~~~~~~~

	Lot of thanks to Nectroom for beta testing ipcsd and motivating me :)

Licence
~~~~~~~

	Copyright (C) 2002 Guillaume Morin (arachne@frgentoo.net)

	This program is free software; you can redistribute it and/or
	modify it under the terms of the GNU General Public License
	as published by the Free Software Foundation; either version 2
   	of the License, or (at your option) any later version.

	See COPYING for details

Advertising
~~~~~~~~~~~

	Visit frgentoo.net, the french gentooist community!

	Web : http://www.frgentoo.net
	IRC : #frgentoo at Freenode
