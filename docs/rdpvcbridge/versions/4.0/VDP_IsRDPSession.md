# VDP_IsRDPSession 
The Agent queries the local system to verify if it is running in an RDP session and returns a TRUE value if it is. 
This includes both Horizon and Microsoft RDP sessions. 

API Signature: 
 `BOOL VDP_IsRDPSession(DWORD sessionID);` 
 
Example: 
 `if (!VDP_IsRDPSession(WTS_CURRENT_SESSION)) { 
    LOG_MESSAGE("We are not currently in an RDP session!\n"); 
 } else if (VDP_IsHorizonSession(WTS_CURRENT_SESSION)) { 
 LOG_MESSAGE(“Invoked from an ongoing Horizon RDP session\n”);  
 } else { 
 LOG_MESSAGE("Invoked from an ongoing Mircosoft RDP session\n");
}`
