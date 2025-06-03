# VDP_IsPCoIPSession 
The Agent queries the local system to verify if it is running in a PCoIP session and returns a TRUE value if it is. 

API Signature: 
`BOOL VDP_IsPCoIPSession(DWORD sessionID);` 

Example: 
 `if (!VDP_IsPCoIPSession(WTS_CURRENT_SESSION)) { 
 LOG_MESSAGE("We are not currently in a Horizon PCoIP session\n");  
 } else { 
 LOG_MESSAGE("Invoked from an ongoing Horizon PCoIP session\n");  
 }`
