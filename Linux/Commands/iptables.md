iptables & ip6tables
====================

Administration tool for IPv4/IPv6 packet filtering and NAT. They are used to set up, maintain, and inspect the tables of IPv4 and IPv6 packet filter rules in the Linux kernel. Several different tables may be defined. Each table contains a number of built-in chains and may also contain user-defined chains.

Each chain is a list of rules which can match a set of packets. Each rule specifies what to do with a packet  that matches. This is called a 'target', which may be a jump to a user-defined chain in the same table.

Firewall Rules
--------------
##### List current rules
```
$ iptables -nL
```


Commands and Parameters
-----------------------

##### Commands
* `-A` : Append rule
* `-I` : Insert rule
* `-D` : Delete rule
* `-L` : List rule
* `INPUT` : Incoming from
* `OUTPUT` : Outgoing to

##### Parameters
* `-s` : Source, e.g. `1.2.3.4`
* `-d` : Destination, e.g. `192.168.0.200`
* `-j` : What to do if target matched rule, e.g. `DROP`
* `-i` : Interface, e.g. `eth0`


Common Usages
-------------

##### Block IP Address
Drop any packet coming from the IP address `1.2.3.4`
```
# iptables -A INPUT -s 1.2.3.4 -j DROP
```

##### Remove blocked IP
```
# iptables -D INPUT -s 1.2.3.4 -j DROP
```

##### Specify an interface such as `eth1`
```
# iptables -A INPUT -i eth1 -s 1.2.3.4 -j DROP
```

##### Block Port
Block all traffics incoming port to 80
```
# iptables -A INPUT -p tcp --destination-port 80 -j DROP
```

##### Block Interface
Where `eth1` is usually for WAN interface
```
# iptables -A INPUT -i eth1 -j DROP
```

##### Block UDP
1. Allow DNS requests to google name servers
* `8.8.8.8` & `8.8.4.4` is google free DNS servers
* `192.168.0.1` is network router usually
  ```
  # iptables -A OUTPUT -p udp --dport 53 -d 8.8.8.8 -j ACCEPT
  # iptables -A OUTPUT -p udp --dport 53 -d 8.8.4.4 -j ACCEPT
  # iptables -A OUTPUT -p udp --dport 53 -d 192.168.0.1 -j ACCEPT
  ```
2. Block all other UDP
* `ip6tables` : for IPv6
  ```
  # iptables -A OUTPUT -p udp -j DROP
  # ip6tables -A OUTPUT -p udp -j DROP
  ```

##### Rate limit to prevent UDP floods
Outbound UDP Flood protection in a user defined chain
```
# iptables -N udp-flood
# iptables -A OUTPUT -p udp -j udp-flood
# iptables -A udp-flood -p udp -m limit --limit 50/s -j RETURN
# iptables -A udp-flood -j LOG --log-level 4 --log-prefix 'UDP-flood attempt: '
# iptables -A udp-flood -j DROP
```

##### Reference Links
* http://www.cyberciti.biz/faq/iptables-block-port/
* http://www.cyberciti.biz/faq/linux-iptables-drop/
* http://security.stackexchange.com/questions/31981/how-can-i-reject-connection-from-lan-and-wan-to-some-ports
* http://blog.thoward37.me/articles/code-snippet-iptables-settings-to-prevent-udp-floods/
