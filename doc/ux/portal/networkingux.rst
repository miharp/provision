.. Copyright (c) 2017 RackN Inc.
.. Licensed under the Apache License, Version 2.0 (the "License");
.. Digital Rebar Provision documentation under Digital Rebar master license
.. index::
  pair: Digital Rebar Provision; UX

.. _rs_networkingux:

Networking
============
This section contains information to the DRP endpoint about all networking settings within the available infrastructure. 

Subnets
-------
This section lists all Subnets discovered in the network. 

Each Subnet contains the following information:

* Locked or Unlocked 
* Name
* Subnet Address
* Start IP Address Range
* End IP Address Range
* Active Time
* Reserve Time 

The top of the page contains a series of blue buttons for additional actions:

* Refresh - Refresh the list of Subnets should a new Subnet be in the system
* Add - Add a new Subnet to the system 
* Clone - Clone a selected Subnet to add to the system 
* Delete - Remove all the selected Subnets

Configure Subnets
-----------------

Configuring Subnets is a critical first step in Digital Rebar Provision operation.  The basic UI will show all configured subnets and provide an easy way to add broadcast subnets based on the known interfaces.

To create a new subnet, click the "Add" button in the header. To edit an existing subnet, first click on the name hyperlink on the table, then click the "Edit" button on the top right.

To create a broadcast subnet, click on the "Use Interface" buttons in the "Add Subnet" panel.

There are two primary types of subnets: broadcast and relay:

  * Broadcast subnets are associated with the addresses provided by the Digital Rebar Provision host system.  Digital Rebar Provision can have multiple DHCP ranges; however, only one subnet can be assigned per interface _and_ the subnet CIDR must include the IP of the interface (the range should NOT).  By convention, subnets associated with an interface will be named as the interface.
  * Relay subnets answer requests forwarded from DHCP relays such as those provided by switches.  These can be any suitable IP range.  Since the Relay subnets are not broadcast, they do not conflict with existing DHCP servers in the environment.

Digital Rebar Provision can operate in a permissive reservation mode or require users to whitelist systems before they are serviced.  The `OnlyReservations` flag will operate as a reservations required (whitelist) mode when true; otherwise, Digital Rebar Provision permissive reservation mode will give out addresses to any valid DHCP request.

In additional to serving IPs, DHCP servers provide critical configuration (aka `DHCP Options <https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#DHCP_options>`_) information to the clients.  Setting Option 67, Next Boot, is essential for Digital Rebar Provision to operate as a Provisioner.  This information includes next boot (67), gateway (3), domain name (15), DNS (6) and other important information.  It is encoded in the responses according to `IETF RFC 2132 <https://tools.ietf.org/html/rfc2132>`_

Leases
------
Leases show individual links between tokens and addresses, created through reservation or subnet strategies. Leases remain valid for short periods of time, and cannot be edited. The expiration time of each lease is visible through the UI. Once a lease has expired, it may be removed.

This page shows a list of Leases available in the system.

Reservations
------------
Reservations link tokens to specific IP addresses. This view shows a list of existing reservations along with tokens and strategies associated with each. Currently, MAC is the only available strategy. Reservations may contain options to be applied to connected servers, which are also visible through the UI.

This page shows a list of Reservations available in the system. 
