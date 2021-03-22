# Introduction

If you are doing a lot of your work in a virtual machine you might have noticed
that VSCode runs quite slowly compared to running it on your Host OS.

This guide shows you with the help of a SSH based VSCode extension
how to work with your file system and environment of your Guest OS
from the VSCode Gui running on your Host OS.

In the guide we show we are running:
* Host OS: Windows
* Guest OS: Ubuntu 18.04.5 LTS
* Virtual machine software: Virtualbox 6.1.4

Depending on how much your setup differs in terms of these 3 things, this
guide may or may not be that useful for you.

# Setup static ip to access Virtualbox instance (Guest OS) from Host OS:
Shutdown any virtualbox Guest OS that might be running


Go to Settings -> Network. Add a second adapter with "Attached to:" set to
"Host-only Adapter". Click OK or whatever so settings are applied.


Start your virtualbox Guest OS



enter 'ip a' in terminal. Now you may get a output similar to this:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:92:0b:bd brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 86363sec preferred_lft 86363sec
    inet6 fe80::a00:27ff:fe92:bbd/64 scope link 
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:58:f6:a8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.102/24 brd 192.168.56.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe58:f6a8/64 scope link 
       valid_lft forever preferred_lft forever
```
Ignoring the 'lo' loopback interface, you can see that you have 2 network interfaces that correspond
to the two network adapters that we have setup in virtualbox settings, in my case you can see the
interfaces are called 'enp0s3' and 'enp0s8'.



From the Host OS try pinging either one of those interfaces, by entering the ipv4 address to the command 'ping' in command prompt. For me it would like this:
To ping enp0s3: 'ping 10.0.2.15'
To ping enp0s8: 'ping 192.168.56.102'

You should only get responses from one of them, take note of this, because the one that you
do get a response to is the ip that you will use to connect from Host OS to Guest OS, the other
one is just so Guest OS gets access to internet and is usually there by default
(unless you have other virtualbox network adapter setup)



In the Guest OS, we will now make sure that the ip to connect from Host OS to Guest OS is static
so it doesn't accidentally change in between restarting the virtualbox.

There is 2 ways you could do this. One is setting it up in 'etc/netplan' where you should have a 
*.yaml file. This is the more modern way to setup network interfaces in ubuntu, but if you are running
older version of ubuntu you can try do a similar setup in 'etc/network/interfaces' instead.
Here I will only show exactally what to write if you are doing the setup in *.yaml file in 'etc/netplan/', so what you write will look slightly different if you do it in 'etc/network/interfaces' instead.

First do a backup of the etc/netplan *.yaml file, in case something goes wrong and you want to rollback. Here is what I put in my *.yaml file in etc/netplan:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:   
      dhcp4: yes
    enp0s8:
      addresses: [192.168.0.100/24]
      dhcp4: false
```

Make sure when you put this in your *.yaml that the interface names matches what you have on your computer.
The ip address that I've set to '192.168.0.100' you can set to whatever you want.



Ping the Guest OS from Host OS in the same way we did in step 5 but now with the new static ip we set, just to make sure things are still working properly.
# SSH from Host OS to Virtualbox instance (Guest OS)

First you can just try to ssh from the Host OS, it might work of the bat.
Run in Host OS terminal: 'ssh <user>@<guest os ip>'

If you get 'ssh: connect to host <guest os ip> port 22: Connection refused'
It could be that your Guest OS doesn't have a ssh server installed.
On ubuntu install it by running 'sudo apt-get install ssh'

Hopefully it works to run 'ssh <user>@<guest os ip>' now.

If you get a message like:
```
The authenticity of host '192.168.56.102 (192.168.56.102)' can't be established.
ECDSA key fingerprint is SHA256:tbLAk74bGuAaP2Dme7KealB2OXluYAtpBBT8S0jPRjw.
Are you sure you want to continue connecting (yes/no)?
```
Just type 'yes' and enter.

# Work in VSCode on files located in Guest OS from Host OS

Follow the information in this link:
https://code.visualstudio.com/docs/remote/ssh