# 3. Names, directories, and finding a PV

Status: outlined

## Job

Explain how a flat namespace of hundreds of thousands of names becomes something an application can query.

## Covers

- What a name needs to carry: device, signal, and enough structure that a stranger can search it.
- Channel Finder as the catalog: channel name, properties, and tags, queried over HTTP. Reading and writing still happen over Channel Access or PV Access.
- recsync as the live feed that fills the catalog. RecCaster loads in a standard IOC. RecCeiver can log, store sqlite, or push to Channel Finder.
- Who consumes the catalog: Phoebus name completion, PV Info, archiver configuration, alarm trees.
- The hole in the feed: LabVIEW, PCAS, and other nonstandard servers do not appear unless someone writes another importer.

## Stays out

- The Channel Access search path and broadcast load. That is chapter 9.
- A deploy guide. Versions and ports live in the companion note.

## Draws on

- Companion note, catalog half: <https://github.com/kgofron/channelfinder-pvmapper>
- Channel Finder docs: <https://channelfinder.readthedocs.io/en/latest/>
- recsync: <https://github.com/ChannelFinder/recsync>
