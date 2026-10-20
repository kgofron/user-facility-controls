# 14. Deployment, change, and on-call

Status: outlined

## Job

Describe what changes between a working IOC and a shift that survives the night.

## Covers

- Where an IOC runs, how a client finds it, and what "deployed" means once chapters 3 and 13 are in place: the process is up, the name resolves, and the directory knows about it.
- EPICS as the operator face for a process that is not an IOC. The worked example is systemdIOC: start, stop, reset a failed state, and read status for a systemd service. The motivating service is Serval, the detector process behind the driver in chapter 10.
- A change that is safe to make during a user shift, and a change that waits.
- What the on-call engineer actually does with the tools from earlier chapters: the screen, the alarm, the archive, the logbook, and a search that is quiet enough to use.
- Troubleshooting a single name: `cainfo` for the host, type, and access rights; caSnooper when the question is who is searching. The comparison of those probes with the name servers is chapter 13. If the searches themselves are the outage, the fix is the name server there, not another probe.
- Handoff to the next shift: what must be written down because the control system will not remember it.

## Stays out

- Site-specific procedures, host names, and ticket systems.
- A pager rotation.

## Draws on

- Chapters 3 through 7, 10, and 13.
- systemdIOC: <https://github.com/kgofron/systemdIOC>
- Published operations talks, if they stay at the level of practice rather than a site's internal runbook.
