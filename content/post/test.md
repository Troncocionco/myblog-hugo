+++
title = "Aruba ACNT - Chapter 1"
description = "ACNT certification notes"
date = 2022/09/12
author = "Giacomino"
+++

# Aruba - ACNT

Endpoint // Networking Devices

Switches - Transparent to endpoints (Endpoint-to-Endpoints happen without each device be aware of a switch in the middle). Layer 2 device forwards Ethernet frames based on destination MAC address

AP **Access Points** - Layer 2 devices: enables wireless user to access wired resources and roma about. AP are translational bridges they accept the wifi frame translate it to ethernet frame and send it to wired network.

Router - Layer 3 device that forward packets based on destination IP address. They maintain a **Route table** where you can find all possible paths and choose the best one.

**Wireless Router** = Switch + Router + Access Point (all in one network device)
They broadcast RF signal, connect the WAN with the LAN

## Out-of-band of Mgmt  vs In-band Mgmt
In-band means relying on the same production network to operate as admin on network devices.
Out of band leverage on a different network to reach those network devices

### Mgmt Port

- Exclusively for monitoring and mgmt
- Complete isolation from data network (user traffic)
- An IP address must be assigned to it
- Protocol (SSH, HTTPS, SNMP, NTP)
- Monitoring system (Aruba NetEdit, OOBM Mgmt PC, AirWave Network Management)

### Console Port

OOB configuration, troubleshooting and mgmt throught direct connection 
- RJ-45 or USB connector
- PuTTY, TeraTerm, SecureCRT
    - Specs for Terminal Emulation
        - Baud rate: 115200
        - Data bits: 8
        - Parity: None
        - Stop bits: 1
        - Not flow control

## Interface & Port Numbering

Format: Member/Slot/Port

- Member used with VSF(Virtual Switching Framework) only [multiple switch act as a virtual single switch]
- Slot used in _modular switches_ with multiple line card (indicates line card number). Fixed switch use line number or slots number 1
- Port: line card/chassis interface number

## Switch Configuration
1. Connection to the device either phycally or remotly
2. Access device CLI

    Switch# 

"Switch" is the **hostname** of the switch
"#" represents the context (what you can view/configure)

3. Prompt modes

**Operator** - Switch **>** some view commands no config

**Manager** - Switch **#**  execute, view commands, no config

**Global** - Switch **(coonfig)#** global config commands

**Interface** - Switch **(config-if)#** sub-context config commands

### Transition between prompt modes

| Transition | Command |
| ----- | ------ |
| Operator  --> Manager | Switch> **enable** |
| Manager --> Global | Switch# **configure terminal** |
| Global --> Interface | Switch(config)# **interface 1/1/1** |
| Inteface --> Global | Switch(config-if)# **exit** or **end** |
| Global --> Manager | Switch(config)# **exit** or **end** |
| Manager --> Operator | Switch# **disable** |
_Transaction from Operator to Global/Inteface prompt are not allowed directly._


- **Switch# ?** - show all available commands in the current context

- **Switch# command ?** - show all available parameter in the current context for that command

_TAB as auto-completion/suggestion feature_


## Regular Operation & TroubleShooting
| Command | Description |
| ----- | ----- |
| Switch# show system  | General System Status Info |
| Switch# show version | Version info for Network OS, Serivece OS and BIOS |
