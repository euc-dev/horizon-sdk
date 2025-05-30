---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# Collecting Logs for Troubleshooting

If you experience any issues on the client endpoint or agent machine, collect the necessary logs to assist your Omnissa support representative in troubleshooting.

## Horizon Client Logs
Follow the appropriate procedure for your client platform to collect the client logs. Each procedure involves the following high-level tasks:<br>
1. Disconnect from the problematic session.<br>
2. Enable detailed logging at the **trace** level.<br>
3. Reconnect to the session and reproduce the issue.<br>
4. Collect the client logs.<br>

### To collect logs for Horizon Client for Windows:

1. Disconnect from the desktop session showing the problem.
2. Open **Registry Editor** as Administrator on the Horizon Client endpoint.
3. Add the following registry keys under:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Omnissa\Horizon\HTML5MMR\WebRTCRedir
```

```reg
"html5mmr.log.webrtc.sharedlib.internal"=dword:00000001
"html5mmr.log.webrtc.allowFullText"=dword:00000001
"html5mmr.log.webrtc.allowThrottle"=dword:00000000
"html5mmr.log.noThrottle"=dword:00000001
"html5mmr.log.webrtc.tracelevel"=dword:00000001
```

4. Reconnect to the remote desktop and reproduce the issue.
5. Collect the **DCT support logs** for Horizon Client for Windows as described in:  
[Omnissa KB 1017939](https://kb.omnissa.com/s/article/1017939#windows-horizon-clients)

---

## Horizon Agent Logs
Use the following procedure to collect DCT support logs on the desktop machine.

### To collect logs for Horizon Agent:
1. On the desktop machine exhibiting the problem issue, open `cmd.exe` as an administrator.
2. Navigate to the DCT log folder.

- For Horizon 8:
```shell
cd "C:\Program Files\Omnissa\Horizon\Agent\DCT"
```
- For Horizon Cloud on Microsoft Azure:

```shell
cd "C:\Program Files\Omnissa\Horizon Agents\Horizon Agent\DCT"
```

3. Run:

```shell
support.bat
```

4. The generated `.zip` folder will appear in the `hzn-sdct` folder on the desktop. Upload this zip for Omnissa Support.

