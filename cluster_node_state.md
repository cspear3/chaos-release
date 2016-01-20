#Various states of nodes that should be monitored and captured for later queries.

# Introduction #

Define states that nodes and cluster can be in. We want to store this information. Idea that you can query what any node(s) were doing at any time, or query for what nodes were in whatever state at a certain time.

Nodes can be in multiple states.

# Details #

node states:

  * up
  * drained in slurm
  * down in slurm
  * idle in slurm
  * allocated in slurm
  * draining in slurm
  * down
  * booting
  * rebooting - node will not come up to a runlevel that can run jobs
  * autoreboot - node will come up to a runlevel that can run jobs and set itself to idle.
  * crash - node is up, but was not rebooted, or shutdown cleanly.
  * shutdown - node was shutdown cleanly
  * mounting - remote filesystems
  * checking - checking hardware / firmware
  * configuring - not yet moving to a run level. Node is running cfengine to configure itself.
  * runlevel A - node has passed checking and can move to runlevel B to run jobs
  * runlevel B - node is mounting remote filesystems, starting slurm and anything else users need. After finishing can move to C. Maybe combine B and C?
  * runlevel C - node has all required stuff mounted started and checked and has been set to idle

Cluster states:

  * maintenance mode
  * running jobs
  * down
  * up