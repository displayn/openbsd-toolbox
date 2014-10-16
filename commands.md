# Users
```
adduser                                 # wrapper script to add users
chsh                                    # change user shell and other info
pw groupadd teamtwo                     # add a group to the system
pw groupmod teamtwo -m <username>       # add a user to a group
/etc/group                              # file to edit groups manually
id                                      # show group membership for current user
```


# System Configuration

```
cat /var/run/dmesg.boot                 # show boot log with info about disks and pci devices
ifconfig                                # show and configure network interface parameters
sysctl                                  # tool to show/set all system/kernel coniguration variables
sysctl -a                               # show all stystem/kernel configuration variables
sysctl hw                               # show hardware related info and settings
sysctl net                              # show all network related info and settings
sysctl hw.model                         # show CPU model
sysctl net.inet.tcp.delayed_ack=0       # disable delayed ack in tcp
```


# System Statistics

```
top                                     # display and update information about the top cpu processes
ps auxwww | grep <processname>          # display process status
systat									# show general overview of load, memory, interrupts, disk io
```


# Packages
```
pkg_info <packagename>                	# search for binary packages
pkg_add -r <packagename>                # install binary package and its dependencies
pkg_info                                # show list of currently installed ports/packages with version info
pkg_add -u upgrade <packagename>        # upgrade a packages or all packages
pkg_add -uvi 
pkg_info <packagename>                  # find out which package installed
```


# Network

```
ifconfig <iface> inet <ip/mask>         # configure IP address on interface
ifconfig <iface> inet <ip/mask> alias   # configure IP address alias on interface
ifconfig <iface> del <ip>               # remove IP address from interface
route add -net default <gw_ip>          # add default route
route add -net <ip/mask> <gw_ip>        # add a custom route for given network
/etc/rc.d/netif restart && \            # restart networking and routing after changing the configuration
/etc/rc.d/routing restart                 without rebooting. Execute in tmux or screen session
netstat -rn                             # display routing table
netstat -an                             # display all connections
netstat -m                              # display buffer usage
netstat -s                              # display extensive statistics per protocol (use -p tcp to only show tcp)
sysctl kern.ipc.numopensockets          # display number of open sockets
vmstat -z | egrep "ITEM|tcpcb"          # number of hash table buckets to handle incoming tcp connections
                                          increase net.inet.tcp.tcbhashsize if hitting the limit
```


# Firewall

```
pfctl -si                               # show current state table and counters (useful for tuning)
pfctl -s state                          # show current content of state table
```