## 1.	Overview:
This document briefly describes a Simple Home or Small Network using Cisco Packet Tracer. This network consists of four PCs connected through a few switches and a router. The major focus of this network is to provide an efficient network with less traffic congestion between internal networking devices.

## 2.	Network representation:
 
This diagram shows how the devices are connected through the network using the networking devices. The IP configuration and network segmentations are explained below.

## 3.	Components:
Device	   Label	              Quantity	  Model
PCs	      PC0,PC1,PC2, PC3	     4	       Generic PC
Printers	 Printer 0, Printer1	  2	       Generic Printer
Switches	 Switch1, Switch2	     2	       2960
Router	   Router 0	             1	       2911

## 4.	IP Addressing Schemes:
•	Router Configuration
Device	    Interface	 IP Address	     Subnet Mask
Router R0	  Gig 0/0	  192.168.10.1	   255.255.255.128
Router R0	  Gig 0/1	  192.168.10.129	 255.255.255.128

•	End Host Device Configurations:
Network A:
Device	    IP Address	   Subnet Mask
PC 0	      192.168.10.2	 255.255.255.128
PC 1	      192.168.10.3	 255.255.255.128
Printer 0 	192.168.10.1 	255.255.255.128

Network B:
Device	    IP Address	     Subnet Mask
PC 2      	192.168.10.130	 255.255.255.128
PC 3       192.168.10.131	 255.255.255.128
Printer 1	 192.168.10.132	 255.255.255.128


## 5.	Step-by-Step Configuration:
5.1 PC Configuration:
  1.	Open the Desktop tab on each PC.
  2.	Go to IP Configuration.
  3.	Assign the respective IP addresses and subnet masks.
•	PC0:
  o	IP Address: 192.168.10.2
  o	Subnet Mask: 255.255.255.128
•	PC1:
  o	IP Address: 192.168.10.3
  o	Subnet Mask: 255.255.255.128

5.2 Router Configuration:
Code:
en
configure terminal 
Interface G0/0
Ip address 192.168.10.1 255.255.255.128
Interface G0/0
Ip address 192.168.10.129 255.255.255.128
 
## 6.	Testing Connectivity:
  1.	Use the Command Prompt on PC0.
  2.	Ping PC3 from PC0 using the command:
    > ping 192.168.10.131

## 7.	Verification:
  Source	Destination	Result
  PC0	    PC3	        Ping Success (4 replies)

