# VDP_IsLegacyHorizonInstalled
The Agent queries the local system to determine which version of Horizon is installed; Omnissa or Legacy. You must check VDP_IsOmnissaHorizonInstalled first and then VDP_IsLegacyHorizonInstalled second. Reversing the order may lead to incorrect results due to drivers installed by Horizon to allow applications that are designed to run on legacy Horizon to run on Omnissa Horizon.

API Signature: 
   `BOOL VDP_IsOmnissaHorizonInstalled();  
    BOOL VDP_IsLegacyHorizonInstalled();`
    
Example:

`If (VDP_IsOmnissaHorizonInstall()) { 
  LOG_MESSAGE(“Omnissa Horizon installed\n”); 
} else if (VDP_IsLegacyHorizonInstalled()) { 
  LOG_MESSAGE(“Legacy Horizon installed\n”); 
} else { 
  LOG_MESSAGE(“Horizon is not installed\n”); 
}`
