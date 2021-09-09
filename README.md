# dynamicReverseProxy for Ocpp chargebox backend


Objective
========

I have thousend equipments (EVSE/Ocpp/Soap/ws) on internet, which are supervised by some backends.
Each equipmement is affected to one backend.
A backend can change the list of equipment it supervise.
Each backend is on a distinct IP (same port(s) )

For simplicity in installation, each equipment is configured with an unique backend URL ( httt:// or w:// ).

the ID of the equipement is not in htt-header : it is in POST body data : Soap Header for http, URI for websocket

So whe must dispose of a reverse-proxy, which can rerouting equipement request/connexion to his backend.
This seem do be a programmable reverse-proxy.
So here is a solution with minimum of developpement.

Solution
========
**A)** a NGINX  revers-proxy, with module LUA (  nginx become programmable ). 
Use of OpenResty for dispose of a complete Nginx config.

**B)** Backend send to a script ( by ssh )  his IP and the list of equipement ID.

**C)** when each backend have send his list, /etc/hosts is updated, white entry like :

```
<IP backend1>   <ID equipmement1>
<IP backend1>   <ID equipmement10>
<IP backend2>   <ID equipmement2>
 . . . .  
```
**D)** basic DNS in Debian distrubution can expose this liste, for nginx usage.

**E1)** Http: Nginx find Id Equipment in the body of each request, and replace FDQN by the ID of the equipement, in the current URL
**E2)** WS: Nginx find Id Equipment in the URI  each request, and replace FDQN by the ID of the equipement, in the current URL

That's it !


Sources provided
===============

a nginx.cong 
-------------
* ddns config
* http route with LUA code ( content_read_by_block )
* ws route, idem

Debian installation
-------------------

debian_install.md

scripts
-------
No sources provided, the lector can improvise :)





