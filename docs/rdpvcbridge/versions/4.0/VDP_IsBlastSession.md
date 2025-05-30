---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# VDP_IsBlastSession 
The Agent queries the local system to verify if it is running in a Blast session and returns a TRUE value if it is. 

API Signature:
 `BOOL VDP_IsBlastSession(DWORD sessionID);` 
 
 Example: 
 `if (!VDP_IsBlastSession(WTS_CURRENT_SESSION)) { 
 LOG_MESSAGE("We are not currently in a Horizon Blast session\n");  }
 else { 
Horizon Blast session\n");
}`