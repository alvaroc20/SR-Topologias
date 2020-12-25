# dmz-skel

It is a basic DMZ topology for performing network security
practices. This setup is composed by 3 guests: router, server and pc1.

By default, vagrant creates a NAT network interface (eth0) to access
the guests. By default, this interface provides connectivity to the
guest, but this setup remove these routes to provide connectivity
through the router guest.

Vagrantfile defines 3 interfaces for the router:

- eth1: bind router to the public network (bridge mode).
- eth2: bind router to the DMZ network.
- eth3: bind router to the MZ network.


