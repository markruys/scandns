# scandns.pl

This script should be pretty straightforward. Feed it a network (ip
address/CIDR or ip address/netmask ) and it scans the dns records of said 
network, reporting theresults to STDOUT. Neat.

Note: This script views the following notations as equivalent:
	
	10.0.0.0/24
	10.0.0.0/255.255.255.0
	10.0.0.0:255.255.255.0

Rather than reinvent the wheel, I cheated and used Net::Netmask. Eventually
I'll write a sub to handle slash/netmask notation, but until then this program
requires the forementioned module, which is available from cpan.

Here's some example output (and no, none of these machines are publicly
routable, so don't even think about it):

~~
nooky:~$ ./scandns.pl 10.0.0.0/24
10.0.0.202 => beauty.zacknetwork.com => 10.0.3.101 
10.0.0.203 => tman.zacknetwork.com => 10.0.3.15 
10.0.0.204 => afterglow.zacknetwork.com 
10.0.0.205 => serenity.zacknetwork.com => 10.0.7.10 
10.0.0.206 => girth.zacknetwork.com => girth.zacknetwork.com has no A record
10.0.0.207 => no PTR record
~~

Note that afterglow's A and PTR records matched. Ideally there shouldn't be
anthing in the third column. If there is, then your forward/inverse records
aren't getting along very well.

