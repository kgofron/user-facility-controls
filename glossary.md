# Glossary

One definition per term. Add an entry when a chapter first needs it. If two chapters disagree, fix the chapters.

| Term | Definition |
| --- | --- |
| Channel Access | The original EPICS network protocol for searching, reading, writing, and monitoring process variables. |
| PV Access | The EPICS 7 protocol for structured process-variable data. It does not replace Channel Access at a facility that still runs both. |
| Process variable (PV) | A named control value served by an IOC or another Channel Access or PV Access server. |
| IOC | Input/Output Controller. The process that loads a record database and serves its PVs. |
| Channel Finder | REST directory of channel names, properties, and tags. It does not answer Channel Access searches. |
| cainfo | Channel Access client that prints, for one name, whether it connected, which host answered, and the type, count, and access rights. |
| pvinfo | PV Access client that prints, for one name, the server and the structure of the value. Not the Channel Finder web page called PV Info. |
| PVXS | The newer C++ implementation of PV Access. Its `pvxinfo` and `pvxget` commands match `pvinfo` and `pvget`. |
| caSnooper | Diagnostic that reports Channel Access search requests seen on the network. |
| recsync | Live feed that uploads an IOC's record list to a receiver, which can fill Channel Finder. Standard IOCs load RecCaster. LabVIEW and other nonstandard servers do not join unless a separate client is written. |
| PVmapper | Channel Access name server. Clients send searches to it; it caches which host owns a PV. It does not store properties or tags. |
| CA Gateway | Proxy between a client network and an IOC network. It is an access boundary. A client on the public side can still cause searches on the private side. |
| areaDetector | EPICS framework for detectors that produce arrays. A driver fills NDArrays. Plugins display, process, and save them. |
| NDArray | The array object areaDetector passes from a driver to plugins. |
| HKL | Reciprocal-space indices used as the coordinates of a diffractometer scan. ioc-hkl exposes the motor-to-HKL calculation as PVs. |
| Phoebus | The current Control System Studio client: displays, the alarm table, Data Browser, and a logbook entry. |
| EDM | Extensible Display Manager. An older EPICS display tool still found on beamlines. |
| MEDM | Motif Editor and Display Manager. Older than EDM, and still found on beamlines. |
| Alarm Handler | The classic EPICS alarm client. It shows a configured alarm tree and accepts acknowledgements. |
| Archiver Appliance | The EPICS archive used to store samples from large numbers of process variables. |
| Channel Archiver | The older index-based EPICS archiver. The Archiver Appliance can still retrieve from some of its data sources. |
| Olog | A logbook service used with Phoebus. A person writes the entry. |
| ELOG | The PSI electronic logbook, used on its own and as a Phoebus logbook plug-in. |
| Scan Server | SNS service that runs a submitted scan against process variables: set, wait, and loop, with pause, resume, and abort. |
| Run control | The start and stop of a numbered neutron acquisition, including a pause when a watched value leaves its range. |
| Bluesky | Experiment orchestration used at NSLS-II and APS. A plan sequences the hardware. The RunEngine makes that plan one run and emits the documents for the dataset. |
| ophyd | Python device layer that maps hardware, usually EPICS PVs, into objects Bluesky plans can use. |
| NeXus | Hierarchical scientific data format used for neutron and X-ray datasets. |
| Personnel safety system | Interlock system that protects people. It is deliberately outside EPICS. |
| Equipment protection | Interlocks that protect hardware. Distinct from personnel safety and from software limits inside EPICS. |
