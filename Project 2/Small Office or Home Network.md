## 1.	Overview:
This document outlines the design and implementation of a network for XYZ company’s new branch near Bonalbo village. The network is designed to support three departments with distinct requirements, ensuring secure and efficient communication within the branch.

## 2. Network Design Requirements
  1.	Devices to be used: One router and one switch (all Cisco products).
  2.	Departmental structure:
      o	Admin/IT
      o	Finance/HR
      o	Customer Service/Reception
  3.	Each department will be in a separate VLAN.
  4.	Wireless network access is required for all users.
  5.	Host devices must obtain IPv4 addresses automatically using DHCP.
  6.	Devices in all departments must communicate with each other.

## 3.	Network Diagram

                    Router (Default Gateway) 
                              |  
                     Switch (Supports VLANs) + Wireless Access Points
                            / | \ 
                      VLAN10 VLAN20 VLAN30   
              (Admin/IT) (Finance/HR) (Customer Service) 

## 4.	IP Addressing Scheme
  Assume the ISP provides a base network: 192.168.1.0/24.

  •	Subnet Calculation:
    Base IP: 192.168.1.0/24
    Number of Subnets: 3
    Number of Subnets= 2^n
      2^n = 3  n=2
      Class C – 255.255.255.0 – 255.255.255.192 /26

    1st Subnet
    Network ID: 192.168.1.0
    Broadcast ID: 192.168.1.63
    Host Range: 192.168.1.0 – 192.168.1.62

    2nd  Subnet
    Network ID: 192.168.1.64
    Broadcast ID: 192.168.1.127
    Host Range: 192.168.1.64 – 192.168.1.126

    3rd   Subnet
    Network ID: 192.168.1. 128
    Broadcast ID: 192.168.1.254
    Host Range: 192.168.1.128 – 192.168.1.254

## 5.Configuration Steps
  5.1 Router Configuration
    1.	Assign IP addresses to the router interfaces.
    2.	Configure sub-interfaces for VLANs and set the respective gateways.
    3.	Enable DHCP service for each VLAN.

  Example Configuration:
    Vlan 10
    Name Admin/IT

    Int range fa01 – fa03
    switchport mode access
    switchport access vlan 10
  
  Trunk Configuration:
    int gig0/1
    switchport mode trunk

  Router Configuration:
    Int g1/0.10
    Encapsulation dot1Q 10
    Ip address 192.168.1.1 255.255.255.192

  DHCP:
    Service dhcp
    Ip dhcp pool Admin-Pool
    Network 192.168.1.0 255.255.255.192
    Default-router 192.168.1.1 
    Dns-server 192.168.1.1 
    Domain-name Admin.com
    Exit

## 5.3 Wireless Network Configuration
  1. Connect wireless access points (APs) to the switch.
  2.	Assign VLANs to APs to segregate wireless traffic.
  3.	Configure SSIDs for each department.


## 6.	Testing
  1.	Verify VLANs using the show vlan command on the switch.
  2.	Ping devices across VLANs to ensure inter-departmental communication.
  3.	Connect wireless devices and verify DHCP functionality.

## 7.	Conclusion
  This design ensures a secure, efficient, and scalable network for XYZ company’s branch, meeting all specified requirements.

