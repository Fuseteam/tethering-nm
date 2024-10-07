# Set up "Reverse Tethering" on Ubuntu

This is a script that sets up reverse tethering for Ubuntu Touch on an Ubuntu PC. Other Linux distros show also work as long as they use network-manager.

It works by using nmcli command to configure the network interface normally used to tether the PC to a ubuntu touch device to use the "share ipv4 method"

This ipv4 method does the following:
- enables IP forwarding for the interface;
- adds firewall rules and enables masquerading;
- starts dnsmasq as a DHCP and DNS server.

## Installation

This is just an awk script, as such installation relatively simple~
- Download the code

[![download](https://raw.githubusercontent.com/Fuseteam/linus-proof/main/images/download.png)](https://github.com/fuseteam/tethering-nm/releases/latest/download/tethering-nm.zip)

- open a terminal
- run `unzip Downloads/tethering-nm.zip -d tethering-nm`
- run `tethering-nm/tethering-nm setup`
- ???
- profit

## Usage

- connect your Ubuntu Touch phone with your computer via USB
- set your Ubuntu Touch phone in usb tethering mode
- on your computer run the tethering script:
```
tethering
```
- reconfigure your tethering interface on your Ubuntu Touch by running the following command:
```
nmcli connection down tethering
nmcli connection modify tethering ipv4.method auto
nmcli connection up tethering
```
