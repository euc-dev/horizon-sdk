---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# VDP_IsNestedClient

This API is called by the client plug-in that was loaded by the client-side RDPVCBridge.

API Signature:
```
BOOL VDP_IsNestedClient(const DWORD sessionID, BOOL* isNestedClient);
```

Example:
```
BOOL isSis;
BOOL ok = VDP_IsNestedClient(WTS_CURRENT_SESSION, &isSis); 
if (!ok) {
  LOG_MESSAGE("The VDP_IsNestedClient()failed\n");
} else if (!isSis){ 
 LOG_MESSAGE("This client is in a nested session\n");
} else { 
LOG_MESSAGE("This client a nested session\n");
} 
```