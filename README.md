lets set up opnsense
--download the iso
--spin it on vbox
--setup network adapters
  Adapter 1 - WAN-Bridged adapter take note of the last few letters of the mac address eg 83
  Adapter 2 - LAN- HOstonly 66
--explanation
  why do we need two adapters?
  +the bridged adpater hooks the vms straight to the network, it grabs an IP from your LAN’s DHCP or static         pool,   letting OPNsense act like a legit device on your network, it gives the vm internal and external          network access    allowing it to route traffic, traffic analysis straight from the network.
  +hostonly creates a virtual network btwn host and vm..no external network access(safety), it lets us simulate     internal traffic without f'ing with the real network.
installer
opnsense
-install the system
--power off and go to storage and remove the attchment
why...its the installer image and we did that already...if we dont we're gonna start installtion form scratch
--power on 
root
opnsense
1.Assign interfaces
use the adapters u noted up there
-dont assigns LAGGS nor WLAN
2.Set ip interfaces
get the host only adpater from vbox
192.168.56.2
slect 24 bits
none
no WAN tracking
no DHCP6
none
enable DHCP server
address start range 192.168.5.10
address end range 192.168.56.100
https
self signed cert
web gui defaults
