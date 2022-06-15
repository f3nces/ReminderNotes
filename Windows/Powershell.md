### PowerShell Transcription

Two ways to activate:

+ Group Policy
+ Registry

```bash
#PowerShell Transcription Logging can be enabled in this way "per-user" via the HKEY_CURRENT_USER registry hive, or across the entire host via the HKEY_LOCAL_MACHINE registry hive
reg add HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\PowerShell\Transcription /v EnableTranscripting /t REG_DWORD /d 0x1 /f

reg add HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\PowerShell\Transcription /v OutputDirectory /t REG_SZ /d C:/ /f

reg add HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\PowerShell\Transcription /v EnableInvocationHeader /t REG_DWORD /d 0x1 /f
```

