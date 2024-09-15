# Fundamentals

To set up networking on a server, your server needs a unique address on the network. For this purpose, Internet Protocol (IP) addresses are used. Currently, two versions of IP addresses are relevant:

1. IPv4  - These are based on 32-bit addresses and have four octets, separated by dots, such as `192.168.10.100`.
2. IPv6  - These are based on 128-bit addresses and are written in eight groups of hexadecimal numbers that are 16 bits each and separated by colons. An IPv6 address may look like `fe80:badb:abe01:45bc:34ad:1313:6723:8798`.

# IP Addresses
To make it easier for computers to communicate with one another, every IP address belongs to a specific network, and to communicate with computers on another network, a **router** is used. A **router** is a machine (often dedicated hardware that has been created for that purpose) that connects networks to one another.

### Private Addresses 
Private network addresses are addresses that are for use in internal networks only. Private networks are one solution(the other being IPv6) to the problem that arrises from the scarcity of available IP address. Some specific IP network addresses have been reserved for this purpose:
-   `10.0.0.0/8` (a single Class A network)
-   `172.16.0.0/12` (16 Class B networks)   
-   `192.168.0.0/16` (256 Class C networks)



When private addresses are used, the nodes that are using them cannot access the Internet directly, and nodes from the Internet cannot easily access them. Because that is not very convenient, **Network Address Translation (NAT)** is commonly used on the router that connects the private network to the Internet. In NAT, the nodes use a private IP address, but when accessing the Internet, this private IP address is replaced with the IP address of the NAT router. Hence, nodes on the Internet think that they are communicating with the NAT router, and not with the individual hosts.
![[Pasted image 20220712064219.png]]

IP Address are broken into two portions.
1. 192.168.1 - The Network Portion
	1. The unique number of your address
	2. The class of your network
2. .14 - The Host Portion
	1. Uniquely identifies the machine. 

Ok, so how do other hosts know which part of the address is the network and which part is host?? This is where subnet masking comes into play. 

### Network Masks
To know to which network a computer belongs, a **subnet mask** is used with every IP address. The **subnet mask** defines which part of the network address indicates the network and which part indicates the node.

Example
192.168.123.132/24 or 255.255.255.0

# Mac Addresses 
Each network card also has a 12-byte MAC address. MAC addresses are for use on the local network (that is, the local physical network or local WLAN, just up to the first router that is encountered); they cannot be used for communications between nodes that are on different networks. MAC addresses are important, though, because they help computers find the specific network card that an IP address belongs to.

# Protocols and Ports
| Port | Service |
| ---- | -------- |
| 80   | HTTP     |
| 22   | SSH         |

# Managing Network Address and Interfaces
Network addresses can be assigned in two ways:

-   Fixed IP addresses -  Useful for servers that always need to be available at the same IP address.
-   Dynamically assigned IP addresses - Useful for end users’ devices, and for instances in a cloud environment. To dynamically assign IP addresses, you usually use a Dynamic Host Configuration Protocol (DHCP) server.

# Validating Network Configuration
## Validating Network Address Configuration

To verify the configuration of the network address, you need to use the `ip` utility. With the `ip` utility, many aspects of networking can be monitored:

-   Use` ip addr` to configure and monitor network addresses. 
	- ip addr add - Specify the device, and the IP address you want to add. 
-   Use `ip route` to configure and monitor routing information.
	- ip route show
-   Use `ip link` to configure and monitor network link state.

>[!WARNING] Changes made with ip are NOT persistent.

# Configuring Network Configuration with nmtui and nmcli

>[!WARNING] Changes made with nm are persistent.


>[!TIP] nmtui has a text interface and nmcli is the command line interface. For the exam, stick with nmtui. When working with network configuration in RHEL 8, you should know the difference between a device and a connection:

-   A **device** is a network interface card.
-   A **connection** is the configuration that is used on a device.

Believe it or not, if an ordinary user is logged in to the local console, this user can make changes to the network configuration. To check your current permissions, use the `nmcli gen permissions` command, as shown in

### NMCLI
>[!TIP] ENsure that the bash-completion RPM package is installed with working with nmcli


# Network Configuration Files
Every connection that you create is stored as a configuration file in the directory `/etc/sysconfig/network-scripts`. The name of the configuration files starts with  
ifcfg- and is followed by the name of the network interface. If you don't like using nmcli or nmtui, you can use the config files. After you're finished editing, just make sure you run `nmcli con up`

# Hostname and Name Resolution

You can change the hostname with one of the following: 
-   Use `nmtui` and select the option Change Hostname.
-   Use `hostnamectl set-hostname`.
-   Edit the contents of the configuration file /etc/hostname.

### Hostname Resolution
Hostname resolution can be configured in `/etc/hosts`. Setting up an /etc/hosts file is easy; just make sure that it contains at least two columns. The first column has the IP address of the specific host, and the second column specifies the hostname. The hostname can be provided as a short name (like server1) or as an FQDN. In an FQDN, the hostname as well as the complete DNS name are included, as in server1.example.com.

If a host has more than one name, like a short name and a fully qualified DNS name, you can specify both of them in /etc/hosts. In that case, the second column must contain the FQDN, and the third column can contain the alias. Example 8-10 shows a hostname configuration example.

### DNS Name Resolution
To specify which DNS server should be used, set the DNS server using `nmcli` or `nmtui`. The NetworkManager configuration stores the DNS information in the configuration file for the network connection, which is in /etc/sysconfig/network-scripts, and from there pushes the configuration to the /etc/resolv.conf file, which is used for DNS name server resolving.

>[!TIP] It is recommended to always set up at least two DNS name servers to be contacted. Why? IF the first server does not answer, then 2nd one is contacted. 

>[!WARNING] Do not edit `/etc/resolv.conf`. It will be overwritten the next time you restart  Network Manager.

To specify the DNS name servers you want to use, you have a few options:
-   Use nmtui to set the DNS name servers. 
-   Set the DNS1 and DNS2 parameters in the ifcfg network connection configuration file in /etc/sysconfig/network-scripts.
-   Use a DHCP server that is configured to hand out the address of the DNS name server.
-   Use nmcli con mod <connection-id> [+]ipv4.dns <ip-of-dns>.

Remeber, when updating your IP address make sure the following are set up:
1. Ip Address
2. Netmask
3. Gateway