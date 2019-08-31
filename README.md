# lldbscripts

This repository contains helper scripts for [lldb](https://lldb.llvm.org) debugging. 

## ignore_signals.py

Automatically configure processes to not stop on SIGSEGV. Similar to the gdb command `handle SIGSEGV noprint`, but the lldb equivalent `process handle --stop false SIGSEGV` cannot be executed until a process has been loaded. Hence the need for a helper script.

### Usage

Add a line similar to this to your `~/.lldbinit` file:

```lldb
command script import ~/git/lldbscripts/ignore_signals.py
```

### Customization

To add other signals to the list, add a line similar to this one in ignore_signals.py:

```python
signals.SetShouldStop(11, False)
```

The number to use can be found for example in [signal.h](https://github.com/freebsd/freebsd/blob/1d6e4247415d264485ee94b59fdbc12e0c566fd0/sys/sys/signal.h#L93).
