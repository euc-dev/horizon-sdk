# How to Use RDPVCBridge SDK

Implementing RDPVCBridge only requires changes to be made on the server-side virtual channel application. There are no changes required on the existing client-side plug-ins.

<!-- insert Agent Side diagram -->

The preceding image is a pictorial view of the application, PCoIP or Blast Server, and 
RDPVCBridge on the agent side. The application and RDPVCBridge run in the same process. The PCoIP or Blast Server runs in its own process.

<!-- insert Client Side diagram -->

The preceding image is a pictorial view of the application's client-side plug-in, RDPVCBridge, PCoIP or Blast Client, and Omnissa Horizon Client on the client side. All the software components run in the same process.

## Prerequisites

You must have the Horizon environment set up and running before you implement RDPVCBridge. For information about setting up Horizon 7 or 8, see the Horizon Administration guide which is part of the [Omnissa Horizon Documentation](https://docs.omnissa.com/category/Horizon_8). For information about setting up Horizon Cloud Service, see the [Omnissa Horizon Cloud Service Documentation](https://docs.omnissa.com/bundle/HorizonCloudServicesUsingNextGenGuide/page/UsingHorizonControlPlanenext-gen-HorizonCloudServiceandCloud-ConnectedHorizon8.html).

To get a better understanding of the required changes to an application, ensure that you have the vchan-ping sample application, which is included in the RDPVCBridge SDK, working before you implement RDPVCBridge for other applications.

## RDPVCBridge - Server Side

On the server side, changes to the top-level header file of the virtual channel plug-in are required.

Make the following changes to the top-level header file:

1.  Define the symbol `MAP_RDPVCBRIDGE`. 

    Defining the `MAP_RDPVCBRIDGE` symbol creates macros that map the Windows WTS* function calls to Horizon VDP_* function calls.

2.  Include the `vdp_rdpvcbridge.h` header file from the RDPVCBridge SDK. For example:
    ```
    #define MAP_RDPVCBRIDGE
    #include "vdp_rdpvcbridge.h"
    ```

3.  Include the source file `vdp_rdpvcbridge_import.cpp` in your application. This file will find, load and fetch the entry points for the RDPVCBridge SDK. 

4.  Recompile your application.

5.  Deploy the application.

## RDPVCBridge - Client Side

On the client side, you do not need to change or recompile any library (.dll, .so, or .dylib) of your virtual channel application. The changes that you must make depend on the type of operating system.

### Windows

1.  Deploy the application plug-in.

2.  Register the application plug-in in the registry.

3.  Add a registry key to enable PCoIP or Blast for the plug-in. The registry key has two values:

    - **Name** - The value is the complete absolute path of the plug-in. 

    - Client versions 2412 and later set Horizon Enabled - The value is 1.
    - Client versions 2406 and earlier set View Enabled - The value is 1. 

**Note:** The `Horizon/View Enabled` registry entry, with value 1, loads the plug-in by rdpvcbridge for both PCoIP and Blast protocols.

For example, you have a virtual channel application called `VChanApp` and `vchan-app-client.dll` is the client-side plug-in. The location of `vchan-app-client.dll` is `C:\VChanApp\vchan-app-client.dll`. 

You must add the following registry key and values:
```
[HKEY_CURRENT_USER\Software\Microsoft\Terminal Server Client\Default\AddIns\VChanApp]
"Name"="C:\\VChanApp\\vchan-app-
```

### Linux

1.  Deploy the application plug-in.

2.  Place the client-side shared-object file in the appropriate folder:

    - Client versions 2412 and later - `/lib/.omnissa/rdpvcbridge' or `~/.omnissa/rdpvcbridge`

    - Client versions 2406 and earlier - `– /lib/.*****/rdpvcbridge' or `~/.*****/rdpvcbridge`

### Mac 

1. Deploy the application plug-in.
2. Place the client-side shared-object file in the appropriate folder:
   - Client versions 2412 and later - `/Library/.omnissa/rdpvcbridge` or `~/.omnissa/rdpvcbridge`
   - Client versions 2406 and earlier – `/Library/.*****/rdpvcbridge` or `~/.*****/rdpvcbridge`
   

