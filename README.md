# Ross Dashboard

Ross Dashboard custom panels.

## PDU Ctrl.grid

Controls USP-PDU-Pro outlets (power on/off, reboot with confirmation) from a
Ross DashBoard touch panel. It does **not** work standalone - DashBoard's
panel scripting can't log into a UniFi controller directly (no way to carry
the cookie/CSRF session UniFi's API requires), so this panel talks to a
small relay service instead of UniFi itself.

That relay is a separate project, meant to run on a Debian host (an LXC
container in this setup): **[hendogg02/pdu-relay](https://github.com/hendogg02/pdu-relay)**.
It handles the UniFi login and exposes simple endpoints the panel calls to
list PDUs/outlets and cycle power. See that repo for install instructions
and its own web UI (setup, live outlet status, power draw).

To use this panel: get the relay running and reachable first, then open
**PDU Ctrl.grid** - it starts on a Settings tab where you point it at the
relay's host/port, and one tab per discovered PDU appears from there.
