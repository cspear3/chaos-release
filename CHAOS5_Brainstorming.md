# CHAOS 5 Brainstorming

### Release Dates ###

GA prior to SC 2010 (November)

Beta to allow Lustre/ZFS file system test July 2010.

### Ideas ###

  * Lustre w/ ZFS
  * IO Forwarding via modified 9P (fault tolerance?)
  * Modified service startup
    * Upstart
    * Possible new cluster run levels
    * Checknode as an init script/package
  * Key management (possible flash storage in node?)
  * RAS/cerebro more functionality / skummee config
  * Get rid of nodeup
  * Simple cluster config / cluster configuration language
  * 12K node support / 48 cores per node
  * GPGPU w/ OpenCL and nvidia drivers
  * KVM & slurm
  * Job container
  * Chaos (rename?, new acronym?)=Centos/SCILinux
  * TOSS=RHEL
  * All packages on an external repository
  * GPL v3 packages
  * Nfsroot config management
  * Nfsroot no reboot for rpm updates (kernel?)
  * Security audit / software & services
  * NFS v4
  * SELinux
  * IPv6 / IPSEC
    * IPoIB ARP storm solution?
  * Krb credential management
  * External documents on doing everything
    * Cookie wiki on stuff we tested
  * Noise testing
    * NTP or something better, Skummee, Slurm, Cerebro
  * GPFS support
  * PanFS support
  * SSD for checkpointing, etc.
  * DNS all IPs, DNSMasq?
  * DHCP all interfaces
  * Modules: MPIs, Compilers, Tools
  * Allow multiple clusters to be managed via 1 node
    * slurm/moab partitions
  * Alternative fabric topologies
  * Kernel splice
  * Firmware management framework
  * Private-mount root per job
  * Check out OSCAR, Rocks, Scyld (penguin)
  * SimCluster
  * Hadoop/HPFS support

### Checknode ###

Things we want to check on a cluster. This may change runlevels, not sure yet.

**cpu MHz** - verify cpus are running at expected speed.

**cpuspeed** - is cpuspeed working. Bios setting could be wrong and cpuspeed can't start.

**swap** - is the amount of swap available expected.

**bios version** - verify bios version is correct. All nodes of the same type should have the same version.

**interface IPs** - verify IP address match for the node

**IB card Firmware version** - verify IB firmware version. All nodes within a IB family should have the same firmware version installed.

**IB link speed** - verify IB card linked at the correct speed.

**hard drive performance** - verify hard drive is ok. A slow hard drive means it is probably going to fail.

**number of memory errors** - check number of memory errors that have occurred. Replace memory that is getting single bit memory errors, or worse multi-bit memory errors.

**ecc** - verify ecc is on, and the correct type is on. ECC types are:
  * S4ECD4ED = ECC with chipkill
  * SECDED = ECC, no chipkill

**amount of memory** - verify all the memory is available.

### Yum Groups ###

Just getting down some thoughts on YUM group structure for CHAOS 5

Base - rpms that go on all node. Maybe this should be extremely minimal and provide more YUM groups.

Slurm - generic slurm rpms, no interconnect specific slurm rpms

Desktop - rpms like openoffice and so on. Maybe we shoot this group in chaos, and move to Base YUM group?

Lustre - lustre client and tools

Lustre.server - lustre server and tools

nfsroot - rpms for booting diskless nodes

openib - rpms for running an OpenIB cluster, this will include Slurm YUM group and add IB specific slurm rpms

opt - rpms that use modules, and install into /opt

opt.openib - rpms that use modules, install into /opt, will require openib YUM group. Should directory structure in /opt have a sub dir with interconnect name?

opt._INTERCONNECT_ - Should we assume that more interconnects may come out, maybe just think 10GigE?

just.works._INTERCONNECT_ - has mpi stuff in system locations so that modules wouldn't need to be used to get mpi working? should match versions that are in /opt

Drivers - Drivers that are cutting edge that we don't usually install, but some people may want to try

FW - Firmware for various motherboards, IB cards, and so on that we have

### 12K cluster point design ###

Attempt to design design CHAOS 5 to scale to 12K nodes. Building a cluster this way is not necessarily a good idea, but will help focus the software development.

12K cluster detail.

18 - 648 port top level IB switches

648 - 36 port leaf switches, 18 links to nodes, 18 links to top level switches, 1 per top level switch

node = quad socket, 12 cores per socket, 48 cores total. 128 GB ram per node

Scalable unit = 324 nodes: 1 mgmt node, 1 login node, 8 gateway nodes, 314 compute nodes

total mgmt nodes = 36

total login nodes = 36

total gateway nodes = 288

total compute nodes = 11304

total node count - 11,664

total core count - 559,872

total memory count - 1,492,992 = 1.5 PB

~ Power 1 node = 1KW\*11664=11.6MW

~ performance = 48cores\*2GHz\*4operations = 384 GF/s\*11664 = 4.478 PF/s