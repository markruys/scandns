# scandns.pl

This script should be pretty straightforward. Feed it a network (ip
address/CIDR or ip address/netmask ) and it scans the dns records of said 
network, reporting theresults to STDOUT. 

Note: This script views the following notations as equivalent:
	
	10.0.0.0/24
	10.0.0.0/255.255.255.0
	10.0.0.0:255.255.255.0

Here's some example output:
~~~
nooky:~$ ./scandns.pl 10.0.0.0/29
ERROR: 10.0.0.202 => beauty.zacknetwork.com => 10.0.3.101 
ERROR: 10.0.0.203 => tman.zacknetwork.com => 10.0.3.15 
OK:    10.0.0.204 => afterglow.zacknetwork.com 
ERROR: 10.0.0.205 => serenity.zacknetwork.com => 10.0.7.10 
ERROR: 10.0.0.206 => girth.zacknetwork.com => no A or CNAME record
ERROR: 10.0.0.207 => no PTR record
~~~

