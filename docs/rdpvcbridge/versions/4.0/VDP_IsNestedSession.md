# VDP_IsNestedSession

When this function is called in the Agent's context (the ideal use case), the Agent sends a message to the Client asking if the Client is running in an ongoing Horizon session.

API Signature:
```
BOOL VDP_IsNestedSession(const DWORD sessionID, BOOL* isNestedSession);
```

Example:
```
BOOL isSis;
BOOL ok = VDP_IsNestedSession(WTS_CURRENT_SESSION, &isSis); 
if (ok) {
   LOG_MESSAGE("VDP_IsNestedSession() failed\n");
} else if (!isSis){ 
   LOG_MESSAGE("The remote client is not in nested session.\n");
} else {
   LOG_MESSAGE("The remote client is in nested session.\n");
}
```
