# Generate Basic NX-OS VXLAN configuration
* Sample Ansible and Jinja templates to generate VXLAN configurations

The code provided in this repository presents a means to use Ansible with Jinja2 templates to
generate configurations that will create a basic VXLAN fabric between Spine/Leaf switches.

This code was generated to work on NX-OSv switches and may need slight modification depending
for use on physical hardware.  The resulting generated code should allow you to copy and paste
straight in config mode on an NX-OS device.

* Scale to your needs

By utilizing and the inventory directory you can generate group and host specific variables to
scale your VXLAN Spine and Leaf environment on the fly.  Need more spine or leaf switches?  Add 
additional directories to host_vars with a new nxos-config.yml for that host and update the 
inventory.yml file vwith the additional spines.  If you wish to remove devices, simply comment out
the line with a # or remove the hosts you don't want from the inventory.yml file.

* What the Ansible code does

This Ansible code will generate configuration for 2 Spines and 4 Leaf switches.  The underlay
network for this environment runs on ISIS and the overlay network use BGP EVPN.  The connectivity
between device is established using "ip unnumbered" using the loopback 0 IP.  The system establishes
one Layer 2 VNI labeled 160020 which is assigned to VLAN 20 on both switches.

* Notes

This code was generated to work on VIRL NX-OSv9000 devices.  It has not been utilized on physical
hardware.  When the code is generated, you will need to copy and paste the config in "configure terminal"
mode on the boxes you are deploying.