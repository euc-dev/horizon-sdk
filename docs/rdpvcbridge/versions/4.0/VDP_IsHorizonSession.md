# VDP_IsHorizonSession

The Agent queries the local system to verify if it is running in a Horizon session and returns a TRUE value if it is. The sessions supported are those using any of the protocols that Horizon supports: Blast, PCoIP, or RDP. The Agent's query returns a FALSE when the local system is not running in a Horizon session, including not being in a remote session or establishing a remote session using a different application, such as Microsoft Remote Desktop Connection. 

API Signature:
```
BOOL VDP_IsHorizonSession(DWORD sessionID);
```
Example:
```
if (!VDP_IsHorizonSession(WTS_CURRENT_SESSION)) {
 LOG_MESSAGE("We are not currently in a Horizon Session! \n");
} else { 
 LOG_MESSAGE("Invoked from an ongoing Horizon session\n");  }
```
