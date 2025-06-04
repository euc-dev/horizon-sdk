# VDP_IsDesktopSession 
The Agent queries the local system to verify if it is running in a remote desktop session and returns a TRUE value if it is.
 API Signature: 
 `BOOL VDP_IsDesktopSession(DWORD sessionID);`

 Example:
 `if (VDP_IsDesktopSession(WTS_CURRENT_SESSION)) { 
     LOG_MESSAGE("Invoked from an ongoing Horizon remote desktop session\n");  
  }`
