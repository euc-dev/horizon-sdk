---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Windows

1.  To change the default logging level, set the following registry entries on both the Agent and the Client systems. The following example changes the logging level to TRACE.

    - Versions 2412 and later:
        ```
        [HKEY_LOCAL_MACHINE\SOFTWARE\Omnissa\Horizon\rdpvcbridge]
        "LogLevel"="trace"
        ```
    - Versions 2406 and earlier:
        ```
        [HKEY_LOCAL_MACHINE\SOFTWARE\V*****, Inc.\V***** VDM\rdpvcbridge]
        "LogLevel"="trace"
        ```
2.  Disconnect from the Horizon desktop, if you are connected, and start the session again.

The log files can be found in the following locations.

## Location of Log Files on a Windows System

<table>
<thead>
<tr>
<th>Log File Type</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr>
<td>Client-side plug-in log file</td>
<td>Versions 2412 and later - 
<br><code>C:\Users\{USER-NAME}\AppData\Local\Temp\omnissa-{USER-NAME}\******-rdpvcbridge-Client-{pid}.log</code><br>
<br>Versions 2406 and earlier - 
<br><code>C:\Users\{USER-NAME}\AppData\Local\Temp\v*****-{USER-NAME}\******-rdpvcbridge-Client-{pid}.log</code></td>
</tr>
<tr>
<td>Agent-side application log file when the application is running under the user account</td>
<td>Versions 2412 and later - 
<br><code>C:\Users\{USER-NAME}\AppData\Local\Temp\omnissa-{USER-NAME}\******-rdpvcbridge-{APP_NAME}-{pid}.log</code><br>
<br>Versions 2406 and earlier - 
<br><code>C:\Users\{USER-NAME}\AppData\Local\Temp\v*****-{USER-NAME}\******-rdpvcbridge-{APP_NAME}-{pid}.log</code></td>
</tr>
<tr>
<td>Agent-side application log file when the application is running under the system account</td>
<td>Versions 2412 and later - 
<br><code>C:\ProgramData\Omnissa\Horizon\logs\******-rdpvcbridge-{APP_NAME}-{pid}.log</code><br>
<br>Versions 2406 and earlier - 
<br><code>C:\ProgramData\V*****\VDM\logs\******-rdpvcbridge-{APP_NAME}-{pid}.log</code></td>
</tr>
</tbody>
</table>
