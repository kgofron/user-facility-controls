# Glossary

One definition per term. Add an entry when a chapter first needs it. If two chapters disagree, fix the chapters.

| Term | Definition |
| --- | --- |
| Channel Access | The original EPICS network protocol for searching, reading, writing, and monitoring process variables. |
| PV Access | The EPICS 7 protocol for structured process-variable data. It does not replace Channel Access at a facility that still runs both. |
| Process variable (PV) | A named control value served by an IOC or another Channel Access or PV Access server. |
| IOC | Input/Output Controller. The process that loads a record database and serves its PVs. |
| Channel Finder | REST directory of channel names, properties, and tags. It does not answer Channel Access searches. |
| recsync | Live feed that uploads an IOC's record list to a receiver, which can fill Channel Finder. Standard IOCs load RecCaster. LabVIEW and other nonstandard servers do not join unless a separate client is written. |
| PVmapper | Channel Access name server. Clients send searches to it; it caches which host owns a PV. It does not store properties or tags. |
| CA Gateway | Proxy between a client network and an IOC network. It is an access boundary. A client on the public side can still cause searches on the private side. |
| Bluesky | Experiment orchestration layer used at NSLS-II and APS. It runs plans above EPICS via ophyd. |
| ophyd | Python device layer that maps hardware, usually EPICS PVs, into objects Bluesky plans can use. |
| NeXus | Hierarchical scientific data format used for neutron and X-ray datasets. |
| Personnel safety system | Interlock system that protects people. It is deliberately outside EPICS. |
| Equipment protection | Interlocks that protect hardware. Distinct from personnel safety and from software limits inside EPICS. |
