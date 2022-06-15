# Essential Tools

[TOC]

## Netcat

```bash
#Example command
nc <ip address> <port>
```

| Flags             | Description                       |
| ----------------- | --------------------------------- |
| **-l**            | Listen for connections            |
| **-n**            | Numeric-only IP addresses, no DNS |
| **-p**            | Specify a port to listen on       |
| **-e** <filename> | Program to exec after connect     |
| **-v**            | Verbose mode                      |

### Connecting to a TCP/UDP Port

+ To check if a port is open or closed
+ To read a banner from the port
+ To connect to a network service manually

```bash
#Example command
nc -nv <ip address> <port>
```

### Listening to a TCP/UDP Port
```bash
#Example command
nc -nlvp <ip address> <port>
```

###  Transferring Files
```bash
#On the Victim Machine
nc -nlvp <ip address> <port> > <path/to/file>

#On the Attacker Machine
nc -nv <ip address> <port> < <path/to/file>
```

### Bind and Reverse Shell
[Bind & Reverse Shell](./3_Exploitation/3.5_Shells)



## Ncat





## Wireshark

[Wireshark_Display_Filters_v1](../CheatSheets/Wireshark_Display_Filters_v1.pdf)
[Wireshark_Display_Filters_v2](../CheatSheets/Wireshark_Display_Filters_v1.pdf)

+ Principais filtros HTTP e HTTPS
  + http.request
  + ssl.handshake.type==1



## TCPdump

