# netdata-ntp-peers

Netdata python module for NTP peers

**Note:** This module is very heavy, only use it for debugging.  
Please use the new version here: https://github.com/rda0/netdata-ntp

The module **ntp_system** uses `ExecutableService` class and the command `ntpq -c readlist` to read the system variables of the ntp daemon. The module **ntp_peers** uses `SimpleService` and a combination of the commands `ntpq -c associations` (to get the current association ids of the peers) in check(). Then it uses command `ntpq -c "readvar <associd>"` to read the peer variables from the ntp daemon. If ntpd is restarted those ids change, which results in returning no data.

Todo:

- Fix ntp_peers returning no data when ntp is restarted
- Merge the 2 plugins into the same menu item in netdata
- Probably clean up type.id, family, context, dimension id?
