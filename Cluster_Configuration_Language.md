#Cluster Configuration Language

# Introduction #

A defined format that would be filled out to create cluster files.

Needs to define

Node
> Name - Name of node, Names to be used on cables

> Node location
> > Logical - Device(s)#,port(s)#
> > > Serial console
> > > mgmt network
> > > Highspeed connection


> Node type - Compute, Mgmt, Router, Login.....

> Node info - CPU MHz, Memory, Memory type, Bios info, FW info

# Example of what works from Speadsheet -> Person -> config files #

```
*Names and location - Used to create slurm.conf and genders file*
U_level Name Type
42 ibsw3
41 ibsw4
40 ibsw5
39 sw1
38 cyc1
37 [e|c|p]graph25 Mgmt
36 [e|c|p]graph26 login
35 [e|c|p]graph27 compute
34 [e|c|p]graph28 compute
33 [e|c|p]graph29 compute
32 [e|c|p]graph30 compute
31 [e|c|p]graph31 compute
30 [e|c|p]graph32 compute

*Ethernet Cable - Not needed for config files, but needed to build a cluster right*
###     SRC             DST     Node_type  Cable_length cable_color CAT
25      egraph25        sw1p1   Compute (1U)    5       blue        CAT5e
26      egraph26        sw1p2   Compute (1U)    5       blue        CAT5e
27      egraph27        sw1p3   Compute (1U)    5       blue        CAT5e
28      egraph28        sw1p4   Compute (1U)    5       blue        CAT5e
29      egraph29        sw1p5   Compute (1U)    5       blue        CAT5e
30      egraph30        sw1p6   Compute (1U)    5       blue        CAT5e
31      egraph31        sw1p7   Compute (1U)    5       blue        CAT5e
32      egraph32        sw1p8   Compute (1U)    7       blue        CAT5e

*Serial Console Cable - Use to create conman.conf files*
###     U_level SRC             DST cable_length cable_color CAT
25      37      cgraph25        cyc1p1  5       white        CAT5e
26      36      cgraph26        cyc1p2  5       white        CAT5e
27      35      cgraph27        cyc1p3  5       white        CAT5e
28      34      cgraph28        cyc1p4  5       white        CAT5e
29      33      cgraph29        cyc1p5  5       white        CAT5e
30      32      cgraph30        cyc1p6  5       white        CAT5e
31      31      cgraph31        cyc1p7  5       white        CAT5e
32      30      cgraph32        cyc1p8  7       white        CAT5e

*power cables - Use to create powerman.conf files*
###     SRC      DST     PDU#   Phase   DST_port Label information Cable_length
30      ibsw3p1  pdu2p47 pdu2   phase6  p47      ibsw3p1:pdu2p47       1.5m
31      ibsw3p2  pdu2p46 pdu2   phase6  p46      ibsw3p2:pdu2p46       1m
32      ibsw4p1  pdu2p40 pdu2   phase5  p40      ibsw4p1:pdu2p40       1.5m
33      ibsw4p2  pdu2p39 pdu2   phase5  p39      ibsw4p2:pdu2p39       1m
34      ibsw5p1  pdu2p32 pdu2   phase4  p32      ibsw5p1:pdu2p32       1.5m
35      ibsw5p2  pdu2p31 pdu2   phase4  p31      ibsw5p2:pdu2p31       1m
36      sw1      pdu2p38 pdu2   phase5  p38      sw1:pdu2p38           1.5m
37      cyc1     pdu2p30 pdu2   phase4  p30      cyc1:pdu2p30          1.5m
38      pgraph25 pdu2p45 pdu2   phase6  p45      pgraph25:pdu2p45      1m
39      pgraph26 pdu2p44 pdu2   phase6  p44      pgraph26:pdu2p44      1m
40      pgraph27 pdu2p43 pdu2   phase6  p43      pgraph27:pdu2p43      1m
41      pgraph28 pdu2p42 pdu2   phase6  p42      pgraph28:pdu2p42      1m
42      pgraph29 pdu2p41 pdu2   phase6  p41      pgraph29:pdu2p41      1m
43      pgraph30 pdu2p37 pdu2   phase5  p37      pgraph30:pdu2p37      1m
44      pgraph31 pdu2p36 pdu2   phase5  p36      pgraph31:pdu2p36      1m
45      pgraph32 pdu2p35 pdu2   phase5  p35      pgraph32:pdu2p35      1m

```

### Other info required for checknode / slurm / genders that we gather ###

> Number of sockets

> Number of cores per socket

> CPU speed

> Firmware versions - bios, IB, 10GigE

> amount of memory

> ECC type

## Format ##

Name through memory would be required, the rest could be blank. Things after ":" could be used by vendor to put in color, distance and so on. Lables for cables would be made from this info like graph1:pdu1p1 for the power cable, or graph1:sw1p1 for the blue 3ft ethernet cable.

```
NAME    NODE_TYPE MHZ  SOCKETS CORES_PER_SOCKET BIOS_DATE MEMORY ECC      LOCATION POWER_PORT NETWORK_mgmt:blue NETWORK_console:red NETWORK_ib
graph1  login     2000 4       6                12/12/09  128    S4ECD4ED rack1U5  pdu1p1     sw1p1:3ft         cyclades1p1:5ft     ibsw1p1:6m
```