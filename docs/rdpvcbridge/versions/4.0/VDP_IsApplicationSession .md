---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# VDP_IsApplicationSession 
The Agent queries the local system to verify if it is running in a remote application session and returns a TRUE value if it is.

 API Signature: 
 `BOOL VDP_IsApplicationSession(DWORD sessionID);`
 
 Example: 
 `if (VDP_IsApplicationSession(WTS_CURRENT_SESSION)) { 
 LOG_MESSAGE("Invoked from an ongoing Horizon remote application session\n");  
 }` 