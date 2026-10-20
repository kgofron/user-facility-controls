# Loading RecCaster in an IOC

Cleaned from the public RecCaster demo and the EPNix RecCaster guide. The path and the PV prefix are placeholders. The demo inside the RecCaster repository builds the module and the IOC together, so its own `configure/RELEASE` has no `RECCASTER` line. An IOC in another top adds that line.

Source: <https://github.com/ChannelFinder/reccaster> (`demoApp/src/Makefile`, `iocBoot/iocdemo/st.cmd`).

## configure/RELEASE

```makefile
RECCASTER = /path/to/reccaster
EPICS_BASE = /path/to/epics-base
```

`EPICS_BASE` stays last, as in any other support module.

## src/Makefile

The application name below is `example`. The public demo uses `demo` for the same two lines.

```makefile
example_DBD += reccaster.dbd
example_LIBS += reccaster
```

`example_LIBS` must also include `$(EPICS_BASE_IOC_LIBS)`, as for any IOC.

## st.cmd

```text
dbLoadRecords("$(RECCASTER)/db/reccaster.db", "P=example:")
```

That database is the sync-status records. RecCaster joins the feed without a RecCeiver address. RecCeiver announces itself, and the IOC answers. Extra environment variables, set with `addReccasterEnvVars` before `iocInit`, are optional.
