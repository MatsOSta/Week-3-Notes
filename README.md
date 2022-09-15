# Week-3-Notes

## Botnets
Logical collection of internet-connected devices.
Targets computers, smartphones, IoT.
Ceded to a third party where each device becomes a bot.

Motivations
Demonstration of knowledge
Fun and Profit
Rented out by CCrime
FOr DDoS
sending spam, crypto mining
IRC (Internet-relay chat) encrypted telnet/ SSH

Design goals:
Master, Zombies, Reflectors, Target
Nothing is written on disk. Straight from network to memory
Zero Dependencies. self-contained binaries.
Staged binaries
vulnerability to be exploited // the exploit
The payload. shell,RAT
Strong encryption for transport-layer comms

TLD4 4.5M devices
Zeus with 3.6 US-based devices
Miriai 380k IoT devices

BYOB (Build your own botnet) github
friendly web-based interface
dynimic generation of payloads
multi platform binaries
optional python payload
remote shells
benchmark in hashes/seconds

encrypted payloads to circumvent gateway inspection
reverse TCP shells allow for operation over NAT
May use TLS for encrypted TCP channel
Obfuscated python script

### Mititgating denail of service attacks 
Tolerance is a possibility, could become expensive
Protection can be enable in at leaste these components
Router. ICMP, IP, BGP configuration, Access control lists - ACLs
Intrusion Detection and prevention mechanisms
Egress traffic inspection may block zombies in the LAN
host-based intruseion Detection - generation of dynamic rules to reconfigure the firewall to block attacker
cloud-based DoS preventsion

##Kernal level mitigating
no standard, IP, TCP UDP are best effort
RFC 791 "internet protocol"  IPv4
RFC 793 "TCP" assumes expected use of flags
OS developers have to handle the issue
Unix
• Increase overall open socket count to 10240
• SOMAXCONN=10240 in /usr/sys/include/sys/socket.h
• Decrease wait window TCPTV_KEEP_INIT in 
  /usr/sys/include/netinet/tcp_timer.h

SYN cookies
Allows a server to avoid dropping connections when the SYN queue fills up
SYN Cookies
• # TCP SYN Flood Protection
• net.ipv4.tcp_syncookies = 1
• net.ipv4.tcp_max_syn_backlog = 2048
• net.ipv4.tcp_synack_retries = 3

Filter out unwanted kernel behaviour in FreeBSD
see slides for breakdown.

Install and IDS in between client and servers
Rules can be written to scab detection
Generates alerts
Distributed content delivery!

static objects can be cached 
images
frontend kits
fonts
javascripts
HTML
movies, music, windows updates, anti-virus updates
Dynamic objects cannot be chached
PHP, Node.js backend code
Databases
Game servers
CAN BE DISTRIBUTED!

## Rootkits
Type of malicious software
Enables access to a computer
masks its existence
root is a reference to rooting, achieving admin-level acess to the OS
typically installed after obtating priviledged access to the system
exploit vulnerabillites
priviledge escalation
password cracking
social engineering

#SYS calls
high level language, c c++
high-level application programming interface (API)
API
WIN32
POSIX API (Unix,MAC OS)
Java API

User mode 
Kernel mode
system call requests priviledged action

##Rootkit detection
difficult
Rootkits subvert the software intended to find it
alternative trusted OS should be used for detection and analysis
signature scanning
difference scanning
memory dump

Removal is complicated, potentially impossible
reinstallation is an option Firmware rootkits surivive OS reinstallation

#Rootkit payload
steal user passwords
credit card information
computing resources
unauthorized activities
looks like ordinary driver
backdoor for remote access
keylogges
botnet zombie

good rootkits
 Valve Anti Cheat • Daemon Tools
• Kaspersky Anti Virus
• KMS Tools
• Computer program debuggers

User-mode rootkit
side by side
inject DLL's
vendor-supplied application extensions
debuggers
message interception
function hooking for hiding running processes

kernel-mode rootkit
highest OS privilege
add or replace core function of the OS
device drivers
loadable modules 
unrestricted execution priviledges
harder to develop and insert

Firmware-level rootkit
inerted into motherboard firmware
Network card
Storage device
the UEFI or BIOS
GPU
USB host controller
intel managment engine

Rootkit method of interception
to stop antirootkit tools
modify code change pointers

uses
system events
system calls
object dispatcher

TDL3
Advanced control and data-flow hijacking techniques
directly loads it code into the windows kernel
good example of how kernel execution can be hooked after bypassing operating system integrity checks
relies on key patterns of the kernel's own architecture
discovered in 2010 - designed for the 32-bit version of windows 7
TDL4 is the bootkit variant successor to TDL3



