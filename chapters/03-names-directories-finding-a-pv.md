# 3. Names, directories, and finding a PV

Status: Channel Finder and recsync drafted. A facility naming convention is still to come.

## Job

Explain how a flat namespace becomes something an application can query, and keep that query separate from a Channel Access search.

## Names

A process variable name is the only handle most clients have. Channel Access can search for a name, connect to the host that owns it, and read or write the value. It cannot answer "which motors belong to this instrument" or "which channels are tagged for the archiver." Those are questions about the namespace. They need a directory.

A usable name carries the device and the signal, in an order a stranger can guess. The convention is local, and this section will come back to it. The directory exists because a convention is not a query.

## Channel Finder

Channel Finder is a directory of channel names. Each entry is one channel, a set of properties (name and value), and a set of tags. A client sends an HTTP query that can match the name, the tags, and the property values. The service returns the matching channels as JSON.

Reading or writing the process variable still happens over Channel Access or PV Access. The directory tells an application which names exist and how the facility has labeled them. It does not sit on the search path, and it does not return a value.

The service is the central-services entry on the official EPICS related-software list. It began as a Brookhaven / NSLS-II and HZB collaboration, to give applications a hierarchical view of a flat namespace. A facility talk from that period reported on the order of 180,000 channels. Later public accounts also place it at FRIB diagnostics and at FREIA. ESS contributors are active in the current repositories.

Phoebus, the Python client `pyCFClient`, and site scripts are the usual callers. PV Info is a web front end that needs nothing except Channel Finder. Links from that page to an archiver, an electronic log, alarm history, or caPutLog are optional. PV Info is in production at the Advanced Light Source.

The questions the directory is for are the ones a screen, an alarm tree, or an archiver configuration already asks:

- Complete a name as an operator types.
- Select every channel with a given tag or property, such as an archive policy or an alarm group.
- Show a human label, a location, or an IOC name next to a channel without encoding all of that in the PV name.

Versions, the Java and Elasticsearch baseline, and the listen port belong in the project documentation and in the companion comparison, not here. They move. The job does not.

## recsync

Someone has to put the records into the directory. recsync is the live feed that does that from standard IOCs.

RecCaster is an EPICS support module loaded in the IOC. It waits for a server announcement, uploads the process database, and stays connected. RecCeiver is a standalone daemon. It announces itself, accepts the upload, and can log it, store it in sqlite, or push it to Channel Finder. After the upload the server keeps the IOC on a ping and drops a client that stops answering.

An upload carries the EPICS base version, selected environment variables, and each record's name, type, description, and `info()` tags. That is enough to build a catalog entry. It is not a copy of the record's value.

RecCaster has to be loaded in the IOC. LabVIEW, PCAS, and other servers that are not standard EPICS IOCs do not join the feed unless someone writes a separate client for the same protocol. Those channels can still be inserted by hand or by another importer. Until then they are absent, and an application that trusts the directory will not offer them.

FREIA reports recsync on every IOC together with Channel Finder. ESS e3 documents the same pair. A Rust implementation and a Java receiver exist beside the Python receiver. The book only needs the split: a module in the IOC, a service that accepts the list, and a plugin that writes Channel Finder.

`cfNameserver` is the one bridge from this catalog to a search. It is a PV Access name server that answers from Channel Finder data filled by recsync. It is younger and less active than the directory. Chapter 10 is where a name server belongs.

## What the directory does not answer

An operator who has one name and wants the host that owns it does not query Channel Finder.

`cainfo`, shipped with EPICS base, is the probe for that question. Point it at a name and it reports whether the channel connected, which host and port answered, the native type, the element count, and the access rights. It is a Channel Access client. Run it once, for one name, while troubleshooting. It does not remember the answer for the next client, and it does not quiet the network.

PVmapper answers the same host question for every client. It is a Channel Access name server: clients send it their searches, it caches which IOC owns the PV, and later clients get the cached host instead of a fresh broadcast. It stores no properties and no tags. Chapter 10 treats it with the gateway and the classic name server, because the problem it solves is search traffic. Chapter 11 names `cainfo`, and caSnooper beside it, as the checks an on-call engineer runs when a name will not connect.

A site that wants both a queryable catalog and quiet searches runs both layers. Channel Finder does not answer a search. PVmapper does not tell an application what a channel is for.

## Still to write

- One naming convention, carried by the two example instruments, enough that a reader can parse a name before searching for it.

## Draws on

- Companion comparison, catalog half: <https://github.com/kgofron/channelfinder-pvmapper>
- Channel Finder: <https://github.com/ChannelFinder/ChannelFinderService>
- Channel Finder docs: <https://channelfinder.readthedocs.io/en/latest/>
- recsync: <https://github.com/ChannelFinder/recsync>
- RecCaster: <https://github.com/ChannelFinder/reccaster>
- PV Info: <https://github.com/ChannelFinder/pvinfo>
- EPICS related software: <https://docs.epics-controls.org/en/latest/software/epics-related-software.html>
