# 13. Networks and the broadcast problem

Status: host-finding comparison drafted. Gateway layout is still to come.

## Job

Explain how a client finds the host that owns a process variable, and which tools answer that question. A catalog query is chapter 3. This chapter is the search.

## A search is a broadcast

A Channel Access client that does not already know the host broadcasts a search. Every IOC on that network looks at the name. One of them answers, or none do. The client repeats the search while the name is missing.

On a large accelerator network that repetition is the load. The published SNS figures for 2024 are about 300 IOCs, about 200 soft IOCs, about 100 operator stations, and more than one million process variables. The background was about 900 UDP search packets per second, roughly 5,000 searches per second, for names that did not exist. Those floods locked VME IOCs and caused downtime.

A tool that prints the host for one name does not remove that load. A tool that answers the search for every client can.

## Tools that find a host

These four are the ones people treat as the same tool. They all touch the question "which host has this name?" They do not give the same answer to the next client.

| | `cainfo` | CA name server | PVmapper | `cfNameserver` |
| --- | --- | --- | --- | --- |
| Question | For this one name: did it connect, which host and port answered, and what are the type, count, and access rights? | Which host should this client use, from a list loaded in advance? | Which host owns this name, remembered from the last search a client asked for? | Which PV Access server has this name, using the Channel Finder catalog? |
| Kind | A client you run once | A name server on the search path | A name server on the search path | A PV Access name server |
| IOC change | None | None. The list is the maintenance. | None. The cache is built from searches. | None. The catalog has to be filled, which is chapter 3. |
| What it remembers | Nothing after it exits | The preloaded PV-to-host list | The host, in memory, while clients are still asking | Whatever recsync and other importers put in Channel Finder |
| What it does not do | Quiet the network | Track IOCs that come and go unless someone reloads the list | Store properties or tags | Answer a Channel Access search |

`cainfo` ships with EPICS base. Point it at a name during troubleshooting. If clients are configured to search a name server, `cainfo` uses that path like any other client, and the host it prints is the IOC that owns the PV.

The classic CA name server is the long-standing EPICS extension. It fits a site whose PV-to-host list can be preloaded. A site whose IOCs restart and whose servers are not all standard IOCs has to maintain that list, and restart the name server when it changes. SNS also hit a long-standing Channel Access protocol-version bug when that name server was built against a newer Base than the oldest IOC.

PVmapper is a Channel Access name server with no database and no change to the IOC. Clients list it in `EPICS_CA_ADDR_LIST`. It forwards a search until the PV is found or clients stop asking, caches the host, and answers later clients from that cache. It does not speak PV Access. It has been on the SNS accelerator network since April 2025. By September 2025 most operator consoles used it. Average search traffic fell by about an order of magnitude, to about 100 packets per second. A second instance is there so the service is not a single point of failure. The two servers use different search intervals so they do not repeat the same long-standing missing names in step. The public release recorded with the comparison of 19 October 2026 is R1.1, 8 March 2026.

`cfNameserver` is the PV Access counterpart that answers from Channel Finder. It has no release in that comparison, and its last public update then was June 2024. Use it when the clients are PV Access and the catalog in chapter 3 is already being filled. It is younger than the directory it depends on.

Channel Finder was set aside for this SNS problem. recsync covers standard IOCs. The accelerator still runs LabVIEW servers and VME IOCs as old as Base 3.14.8.2, so a feeder on every server was not practical. The catalog remains the right tool for properties and tags. It is the wrong tool for the search path.

## Neighbors that are not name servers

CA Gateway is the usual boundary between a client network and the IOC network. It keeps most clients off the broadcast domain. It is not a directory of names. SNS already runs one. A client on the public side of that gateway can still cause the gateway to search inside the private network. A name server is the tighter fix when the load is repeated searches for missing names. PVA Gateway is the same boundary for PV Access.

caSnooper decodes Channel Access search requests. It reports who is searching. It does not answer the search. SNS used it, then built a longer-running traffic analyzer. Chapter 14 is where an on-call engineer runs `cainfo` or caSnooper. If those probes show that the searches themselves are the outage, the fix is a name server, not another probe.

`pvlist`, shipped with PV Access, enumerates servers, and then the names on a server it can already see. It is a discovery check, not a directory and not a name server. `pvxlist` is the PVXS command for that check. `pvxvct` watches PV Access search and beacon traffic, which is the PV Access cousin of caSnooper. The command pairs, including `pvinfo` and `pvxinfo`, are the table in chapter 2.

## Still to write

- How a facility decides the boundary a gateway draws, without host names or addresses.

## Draws on

- Companion comparison, search-path half: <https://github.com/kgofron/channelfinder-pvmapper>
- Vodopivec and Cashion, ICALEPCS 2025, TUBR004. <https://proceedings.jacow.org/icalepcs2025/pdf/TUBR004.pdf>
- PVmapper: <https://github.com/klemenv/PVmapper>
- CA name server: <https://epics.anl.gov/extensions/nameserver/index.php>
- CA Gateway: <https://github.com/epics-extensions/ca-gateway>
- cfNameserver: <https://github.com/ChannelFinder/cfNameserver>
- caSnooper: <https://epics.anl.gov/extensions/caSnooper/index.php>
