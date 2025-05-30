---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# VDP_GetSDKVersion

This function returns the current version of Horizon stored in the DLL properties, for example, "8.1.0".

API Signature:
```
BOOL VDP_GetSDKVersion(const DWORD sessionID,
    PCHAR localVersionBuffer,
    const ULONG localVersionBufferSize, 
    PULONG pLocalVersionResultStrSize,
    PULONG pLocalVersionNum,
    PCHAR  remoteVersionBuffer,
    const ULONG remoteVersionBufferSize, 
    PULONG pRemoteVersionResultStrSize,
    PULONG pRemoteVersionNum);
```

Example:
```
char   localVersionStr[1024];
ULONG  localVersionStrLen = ARRAYSIZE(localVersionStr);
ULONG  localResultStrSize = 0;
ULONG  localVersionNum = 0; char   remoteVersionStr[1024];
ULONG  remoteVersionStrLen = ARRAYSIZE(remoteVersionStr);
ULONG  remoteResultStrSize = 0;
ULONG  remoteVersionNum = 0;
BOOL ok = VDP_GetSDKVersion(WTS_CURRENT_SESSION,
        localVersionStr, localVersionStrLen,
        &localResultStrSize,  &localVersionNum,  
        remoteVersionStr, remoteVersionStrLen, 
        &remoteResultStrSize, &remoteVersionNum);
If (!ok) { 
 LOG_MESSAGE("VDP_GetSDKVersion () failed\n");
 } else { 
 LOG_MESSAGE("Local SDK version: v%d - v%s\n", localVersionNum, localVersionStr);

 // Note: remoteVersionNum will be 0 if not in a Horizon session  if (remoteVersionNum != 0) { 
 LOG_MESSAGE("RemoteSDK version: v%d - v%s\n", 
 remoteVersionNum, remoteVersionStr); 
 } 
} 
```