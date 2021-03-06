**3COM switches backup script**
===================

This script connect to a list of 3COM switches for initiating a backup command to a TFTP server.
It use Telnet protocol and the login should be the same all on switches that the script will go.
It require an TFTP server where the backups will be saved.
Run on 4200, 4400, 4500 and 5500 3COM switches.

How to use it
-------------

You need to set few variables :

	tftp_server : IP of tftp server where the backups will be saved
	timeout : time in seconds where we considering that there is a timeout. Be careful to not put too little value, TFTP backup from a switch can take over a minute (the generation time of released file)
	log_file : name of output file for script
	hosts_file : name of file where they are IP address of Avaya switches
	telnet_port : Obvious parameters =)

----------

Input file for switches list
-------------

You need to have a file where they are all switches's IP. He must to be in the same directory with the script. Example of input file :

	# 1 For 3COM 4200 | 4400 | 4500
	# 2 For 3COM 5500
	# 3 For HP A5500
	# Right like this model:name:ip
	# Don't forget ":" separator

	1:switchtest1:192.168.1.2
	2:switchtest2:192.168.1.3
	2:switchtest3:192.168.1.4
	3:switchtest4:192.168.1.253

The script verifie that the IP address is valid.
There is no problem if the file have few texts BUT a line that contains an IP address must only contain it.

Log file
-------------
The script generate a file named that contains the results of all tests for all the hots.
Example of result file :

    18/08/2016 11:30:07 192.168.1.2 switchtest1 : Succesful
    18/08/2016 11:31:24 192.168.1.3 switchtest2 : Failure - connection refused
    18/08/2016 11:31:25 : End of script
