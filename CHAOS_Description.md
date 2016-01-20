## What is CHAOS? ##

CHAOS is a CentOS derived operating system for Linux clusters,
primarily those designed to run MPI programs, but also for visualization
clusters, Lustre file system server clusters, and technical desktop systems.
Early releases of CHAOS `[1,2,3]` were based on Red Hat Linux and used
exclusively in-house at Lawrence Livermore National Laboratory.

| **Name**    | **Date** | **Base OS** | **Architectures** | **Interconnects** |
|:------------|:---------|:------------|:------------------|:------------------|
| CHAOS 1.0   | July 2002 | RHL 7.3     | i386              | Elan3             |
| CHAOS 2.0   | July 2004 | RHEL 3      | i386,ia64         | Elan3,Elan4       |
| CHAOS 3.0   | Oct 2005  | RHEL 4      | i386,ia64,x86\_64 | Elan3,Elan4,Infiniband |
| CHAOS 4.0/TOSS 1.0 | Feb 2008 | RHEL 5      | x86\_64           | Infiniband        |
| CHAOS 5.0/TOSS 2.0 | est. Jan 2011 | CentOS 6/RHEL 6 | x86\_64           | Infiniband        |

In 2008, distribution was extended to the Sandia and Los Alamos
National Laboratories in support of a joint tri-lab cluster procurement.
CHAOS 4.0 was thus given the external moniker of TOSS 1.0.
TOSS `[4]` stands for Tripod Operating System Software.

CHAOS 5.0 will be based on the freely redistributable CentOS operating system
and be made available for public download, while TOSS 2.0 will continue to be
based on Red Hat Enterprise Linux and used internally.  CHAOS and TOSS will
be functionally equivalent, but CHAOS will have all non redistributable components,
such as third party compilers, stripped.  Support for CHAOS will be on a best effort basis.

## Why CHAOS? ##

CHAOS a bundling of software and an
associated process that made our lives more sane at LLNL for several years
as we increased our Linux cluster deployments.  It is not necessary to run CHAOS
in order to leverage its HPC components such as the SLURM resource manager,
Lustre file system, and admin tools.  These are
available as open source which any site could integrate into their
environment.  The main reasons it may be useful to run CHAOS are:

  * Each CHAOS release is subjected to strenuous integration testing on large clusters.
  * Deficiencies uncovered by the diverse HPC workload at the labs must be addressed quickly by maintenance releases.
  * CHAOS runs on hardware that is regularly refreshed.
  * CHAOS security defects are addressed expeditiously.
  * CHAOS contains a selection of software that represents years of experience running large clusters (Linux and otherwise).

In summary, the key benefit of CHAOS is that it is geared towards production HPC computing environments.  On the other hand, this fact may be a negative for those
engaged in system software research and development.
For example the CHAOS kernel usually lags far behind kernel.org releases,
and contains many patches, making it a poor platform for developing new kernel facilities.

## What is Included? ##

These are the major components that we focus on when building CHAOS,
as opposed to the things that just work in the base OS and are brought along:
  * modified kernel
  * SLURM resource manager (job launch and batch management)
  * Lustre parallel file system (clients and servers)
  * Cluster sys admin tools (pdsh, powerman, conman, genders, skummee/netsnmp, cerebro, etc.),
  * MPI and associated development environment.

## What is Not Included? ##

Not a lot of effort has gone into including the various scientific libraries
that many of our customers use.  This is because it seems every site has a
tradition of providing these to users in a different way, and often projects
will want to lock in a particular version and just pull it into their build
tree anyway.  That said, some components have to be packaged and included
just to facilitate reproduceable testing, and to this end we provide a few
of them primarily designed to install into /opt, wrapped with environment
modules.  We try to keep them out of the default environment so omissions
in the user runtime environment LD\_LIBRARY\_PATH setup for example exhibit
as a hard failure rather than the more subtle one you might get from running
the wrong version of an improperly versioned dynamic library.

Non-free software such as non-GNU compilers, math libraries, totalview
debugger, etc. are not included in CHAOS due to redistribution restrictions.
We do package some of these tools for TOSS and could provide spec files and
such should people find that to be useful, but licensing forbids us to
freely redistribute these packages.

## What is the CHAOS Release Cycle? ##

Although for brevity the table above only lists our major releases (X.0),
we also do minor releases (X.1, X.2, ...) that track upstream update releases.
These occur about every six months.

Occasionally we may delay a major release until the first or second upstream
update comes out if we feel our release is not yet stable.  After the major
release, however, upstream update releases are rigorously tracked,
with our minor release lagging by a few months.

Between minor releases, we do TOSS bugfix/security updates on an as-needed
basis.  These updates will be provided immediately in the CHAOS releases
as well.

Major and minor CHAOS releases are gated by rigorous testing on real systems,
including times where we steal one of our largest production systems for a
week or so and try out the new software on it.  This will include, for example,
giving the Lustre file system a serious round of beatings, and running many
large scientific apps over and over checking the results.  After the three
labs sign off on a TOSS release, the public CHAOS release will be made.
Other than being rebased on CentOS and omitting some software with licensing
restrictions, CHAOS will be identical to TOSS.

## References ##

`[1]` [Building CHAOS: An Operating System for Livermore Linux Clusters](https://computing.llnl.gov/linux/ucrl-id-151968.html)
by Dunlap and Garlick.

`[2]` [Linux Project report](https://computing.llnl.gov/linux/ucrl-id-150021.html)
by Dunlap and Garlick.

`[3]` [Achieving Order through CHAOS: the LLNL HPC Linux Cluster Experience](https://computing.llnl.gov/linux/ucrl-jc-153559.html)
by Braby, Garlick, and Goldstone.

`[4]` [Common Tri-Lab Capacity Computing Moves Closer to Goal](http://www.sandia.gov/NNSA/ASC/enews/1207/1207trilab-capacity.html),
Press Release, Sandia National Laboratory.