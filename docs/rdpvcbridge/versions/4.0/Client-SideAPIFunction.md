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
if (ok == FALSE) {
   LOG_MESSAGE("The VDP_IsNestedClient() Failed! \n");
   return;
}
if (isSis == FALSE) {
   LOG_MESSAGE("This Client is Not in Nested Session. \n");
} 
else {
   LOG_MESSAGE("This Client is in Nested Session. \n");
}
```
