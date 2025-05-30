---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# Overview of the Omnissa Horizon Session Enhancement SDK

With the Omnissa Horizon Session Enhancement Software Development Kit (SDK), you can develop applications that communicate between a client and a remote desktop over a Horizon connection using the Blast Extreme or PCoIP display protocol.

The SDK contains resources such as documentation, include files, and code samples, to help you develop applications that use the Omnissa Horizon Session Enhancement API.

## Introduction to the API

The Omnissa Horizon Session Enhancement API specifies how the client side and the desktop side of an application can communicate over a Horizon connection. All interactions with the API are asynchronous.

Any software that uses the Horizon Session Enhancement API must have two components:

- **Application**  
This is the code that runs on a remote desktop.

- **Plug-In**  
This is the code that is installed on a client.

The Horizon Session Enhancement API consists of two distinct APIs:

- **Remote Procedure Call (RPC) API**  
The RPC API provides an asynchronous, callback-driven communication channel between applications that run on a remote desktop and a plug-in that runs on a client. The RPC API also handles the marshaling and un-marshaling of parameters.

- **Overlay API**  
The Overlay API solves the problem of displaying rendered images on the client. Images appear to a user as a local window on the remote desktop.

### OpenSSL Issue

The Horizon Session Enhancement API dynamically loads the OpenSSL library to implement its security features. If a software's application and plug-in components also dynamically load the OpenSSL library in the same way as the Horizon Session Enhancement API, you must adhere to the following rules to prevent crashes or exceptions.

1. Plug-in components must not call the `CRYPTO_set_locking_callback()`, `CRYPTO_set_id_callback()`, and `CRYPTO_set_add_lock_callback()` functions since the `remotemks` service already calls these functions.

1. Application components must set up the preceding callbacks before loading the Horizon Session Enhancement API library. They must also ensure that those callbacks are valid before unloading the Horizon Session Enhancement API library.

1. If the code is shared by both the plug-in and application components, you must call the preceding three callback functions if `CRYPTO_get_locking_callback()` returns `NULL`. You must call those three functions to set callbacks at the same time.

### Supported Versions of Horizon Software

The Horizon Session Enhancement API supports the following types of deployments.

- Horizon pods running Horizon 7 or Horizon 8 (Horizon 2006 and later) software.

    To support the latest features and interfaces of the Horizon Session Enhancement API, ensure that your Horizon pods are running on the latest release version of Horizon 7 or Horizon 8.

- First-gen Horizon Cloud Service on Microsoft Azure pods.

    To support the latest features and interfaces of the Horizon Session Enhancement API, ensure that your first-gen Horizon Cloud pods are running on the latest release version of the pod manifest.

- Horizon Cloud Service next-gen Azure Edge deployments.

**Note:** If your deployments are running on an older release version of Horizon software or of the first-gen Horizon 
Cloud Service on Microsoft Azure pod manifest, some features and interfaces of the Horizon Session Enhancement API are not supported.

### Supported Client Operating Systems

The Horizon Session Enhancement API supports all Windows, Linux, and Mac operating systems that the Horizon Client software supports. For more information about supported operating systems, see the [Omnissa Horizon Client Documentation](https://docs.omnissa.com/category/Horizon_Clients).

## What's New in Omnissa Horizon Session Enhancement SDK 4.0

The following list summarizes the new features and changes found in version 4.0 of the Omnissa Horizon Session Enhancement SDK.

- This version of the SDK supports the new Omnissa-branded stack and is also backwards compatible with the older version as fallback. 

- A new screen capture interface has been introduced to assist with capturing the contents of the Horizon client window.

## Key Concepts of Omnissa Horizon Session Enhancement 

To effectively use the Omnissa Horizon Session Enhancement API, it is important to become familiar with the key concepts in Horizon Session Enhancement.

### Connection

A connection refers to a Horizon session over the Blast Extreme or PCoIP protocol. You cannot alter a connection through the Horizon Session Enhancement API, but you can determine the current state of a connection. If a connection is not in the connected state, no action can be taken with the API. 

You can receive notification of a change in a connection's state using `VDPService_ChannelNotifySink` through the `v1.OnConnectionStateChanged` callback. You can also retrieve the current state of a connection using the `v1.GetConnectionState` method that is found in the `VDPService_ChannelInterface` API.

### Channel

A channel represents the link between a remote application and a local plug-in. The state of a channel is not necessarily the same as the state of a connection.

You can receive notification of a change in the state of a channel through the `VDPService_ChannelNotifySink` function that you register with the channel. The `v1.OnChannelStateChanged` callback delivers the state change. You can query the current state of a channel using the `v1.GetChannelState` method in `VDPService_ChannelInterface`.

### Side Channel

A side channel represents an additional link between a remote application and a local plug-in. A side channel belongs to a channel object and is set up via channel. A side channel can only be established after a channel object is connected. A

 side channel is designed to reduce application response time when there is network congestion in the main channel. For example, an application can use the main channel to transfer real-time control messages and use the side channel to transfer large amounts of user data.

### Channel Context

A channel context is a wrapper for the parameters and return values of a remote call. A channel context holds all of the information for the receiver of a remote call to determine which method is requested. Interaction with the channel context is done using `VDPRPC_ChannelContextInterface`.

### Overlay

An overlay is a window or image that is displayed over another so that the image or window overlay appears to be part of the underlying UI. This is typically done for video that plays locally, but needs to appear as if it is playing on the remote desktop.

### Remote Procedure Call

A remote procedure call (RPC) is an invocation of a method on a non-local machine. Typically, the remote machine publishes a set of methods that it responds to, and the client invokes the methods through some channel. A call to `v1.Invoke` initiates an RPC.

### Sink

A sink is a structure of function pointers and is used to communicate asynchronously with user code via callbacks. Each API call has one or more sets of sinks. The user must register the sinks to receive the necessary callbacks that give the user important information about state changes or events.

### Variant

To ease cross-platform communication, all parameters that are used with the VDP RPC API are wrapped in the VDP_RPC_VARIANT data type. This data type contains an identifier that indicates the type of data in the structure and the data itself. The use of variants is done through `VDPRPC_VariantInterface`.

## Omnissa Horizon Session Enhancement Program Flow

A typical Horizon Session Enhancement program flow involves the initialization of an application, a plug-in, threads, and a channel. It also includes sink registration, the calling of RPC and Overlay API methods, and shutting down.

### Application Initialization

The user controls the startup of the remote side of the Horizon Session Enhancement system. 

Upon application launch, the user code calls the `VDPService_ServerInit` method and gets the VDP_SERVICE_QUERY_INTERFACE structure. The user code then calls the `QueryInterface()` method to fetch all the interfaces that it needs to do its work.
 
**Note:** If `QueryInterface()` returns `FALSE`, your Horizon software version does not support the function interface that you are trying to fetch.

### Plug-In Initialization

On the local side, it is the Horizon Session Enhancement system that initializes the plug-in code. In the `VDPService_PluginInit` call, the user code must store the passed-in reference to the VDP_SERVICE_QUERY_INTERFACE structure and use it to request all the interfaces that it needs. At this point the user code is only loaded. 

Once the matching application for the loaded plugin starts, `VDPService_PluginCreateInstance` is called. In this callback, the user may return a pointer that is returned in each callback, so that the user code can maintain its state. 

To match a plug-in and an application, VDPService calls the plug-in's `VDPService_PluginGetTokenName` method and compares the string that is returned with the string that is given by the application. Before returning from the `VDPService_PluginCreateInstance` callback, the user code must call `v1.Connect` in `VDPService_ChannelInterface`.
 
**Note:** Due to a limitation in the underlying protocol used, the TokenName variable must be less than 16 bytes in length.

### Sink Registration

To receive callbacks from the Horizon Session Enhancement system, you must register sinks for different notifications. 

The first sink to register is `VDPService_ChannelNotifySink`. This sink notifies you of changes to the connection state, the channel state, and when the application has created an object. For more information about object creation, see Channel Object. <!--add link-->

To register the sink, use the `v1.RegisterChannelNotifySink` method in `VDPService_ChannelInterface`. After the sink is registered, you receive a handle for that sink that you can use to unregister the sink. You must register `VDPService_ChannelNotifySink` before you call `v1.Connect` to ensure that you receive a notification when the channel is available.

After you register `VDPService_ChannelNotifySink`, you most likely will not receive a callback for a connection state change. This is because by the time the application or plug-in is started, the connection is likely to be in the connected state. To confirm that the connection is in the proper state prior to any actions, use the `GetConnectionState` method.

In addition to VDPService_ChannelNotifySink, the following sinks exist:

- `VDPRPC_ObjectNotifySink`  
This is for individual channel objects. 

- `VDPRPC_RequestCallback`  
This is for callbacks for each RPC call.

- `VDPOverlayGuest_Sink`  
This is for important overlay notifications for the guest.

- `VDPOverlayClient_Sink`  
These are for important overlay notifications for the client.

### Thread Initialization

On the application side, the main thread is the one that the user calls `VDPService_ServerInit` on. 

On the plug-in side, the main thread is the one that the `VDPService_PluginCreateInstance` callback is received on. 

For other threads, you must call `ThreadInitialize` before you call any other method in the RPC APIs or the Overlay APIs.

If a thread is no longer needed, you must uninitialize it by calling the `v1.ThreadUninitialize` method.

### Channel
For communication to occur, the channel between the application and the plug-in must be active. To initialize the channel connection, call the `v1.Connect` method. It must be called on both sides of the connection for each channel. To shut down a channel, call the `v1.Disconnect` method.

After you call `v1.Disconnect`, or whenever the channel is in a disconnected state, you must free all your channel objects using the `v1.DestroyChannelObject` method. If the channel is connected again, you must recreate any required objects.

### Query Interface

`QueryInterface()` returns an interface, or a structure of function pointers. Both applications and plug-ins must call Q`ueryInterface()` to retrieve the necessary interfaces.

The query interface data type VDP_SERVICE_QUERY_INTERFACE is a structure that is defined in `vdpService.h`. The application and the plug-in receive a reference to this structure differently. 

The structure has two members: a version attribute, and a function pointer. The version attribute notifies the user's application which version of the APIs are available. The function pointer is how the user's code will access the other APIs in the system. The function pointer has the following definition:
```
Bool (*QueryInterface) (const GUID *iid, void *iface);
```
The `QueryInterface()` function fetches the functions that the user needs to interact with the 
Horizon Session Enhancement API.
 
**Note:** If `QueryInterface()` returns FALSE, your Horizon software version does not support the function interface that you are trying to fetch.

#### Horizon Session Enhancement GUIDs

The following table lists the GUIDs that are defined by Horizon Session Enhancement and the function lists that the GUIDs return.

<table>
<thead>
<tr>
<th>GUID</th>
<th>Returned Function List</th>
<th>Version</th>
<th>Header File</th>
</tr>
</thead>
<tbody>
<tr>
<td>GUID_VDPService_ChannelInterface_V1</td>
<td>VDPService_ChannelInterface</td>
<td>v1</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPService_ChannelInterface_V2</td>
<td>VDPService_ChannelInterface</td>
<td>v2</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPService_ChannelInterface_V3</td>
<td>VDPService_ChannelInterface</td>
<td>v3</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPService_ChannelInterface_V4</td>
<td>VDPService_ChannelInterface</td>
<td>v4</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_ChannelObjectInterface_V1</td>
<td>VDPRPC_ChannelObjectInterface</td>
<td>v1</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_ChannelObjectInterface_V2</td>
<td>VDPRPC_ChannelObjectInterface</td>
<td>v2</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_ChannelObjectInterface_V3</td>
<td>VDPRPC_ChannelObjectInterface</td>
<td>v3</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_ChannelObjectInterface_V4</td>
<td>VDPRPC_ChannelObjectInterface</td>
<td>v4</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_ChannelContextInterface_V1</td>
<td>VDPRPC_ChannelContextInterface</td>
<td>v1</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_ChannelContextInterface_V2</td>
<td>VDPRPC_ChannelContextInterface</td>
<td>v2</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_VariantInterface_V1</td>
<td>VDPRPC_VariantInterface</td>
<td>v1</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPService_ServerInterface_V1</td>
<td>VDPOverlay_ServerInterface</td>
<td>v1</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPService_LocalJobInterface_V1</td>
<td>VDPService_LocalJobInterface</td>
<td>v1</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPService_ObserverInterface_V1</td>
<td>VDPService_ObserverInterface</td>
<td>v1</td>
<td>vdpService_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_StreamDataInterface_V1</td>
<td>VDPRPC_StreamDataInterface</td>
<td>v1</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPRPC_StreamDataInterface_V2</td>
<td>VDPRPC_StreamDataInterface</td>
<td>v2</td>
<td>vdprpc_interfaces.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_GuestInterface_V1</td>
<td>VDPOverlay_GuestInterface</td>
<td>v1</td>
<td>vdpOverlay.h</td>
</tr>    
<tr>
<td>GUID_VDPOverlay_GuestInterface_V2</td>
<td>VDPOverlay_GuestInterface</td>
<td>v2</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_GuestInterface_V3</td>
<td>VDPOverlay_GuestInterface</td>
<td>v3</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_GuestInterface_V4</td>
<td>VDPOverlay_GuestInterface</td>
<td>v4</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_ClientInterface_V1</td>
<td>VDPOverlay_ClientInterface</td>
<td>v1</td>
<td>vdpOverlay.h</td>
</tr>    
<tr>
<td>GUID_VDPOverlay_ClientInterface_V2</td>
<td>VDPOverlay_ClientInterface</td>
<td>v2</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_ClientInterface_V3</td>
<td>VDPOverlay_ClientInterface</td>
<td>v3</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_ClientInterface_V4</td>
<td>VDPOverlay_ClientInterface</td>
<td>v4</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPOverlay_ClientInterface_V5</td>
<td>VDPOverlay_ClientInterface</td>
<td>v5</td>
<td>vdpOverlay.h</td>
</tr>
<tr>
<td>GUID_VDPScreenCapture_Interface_V1</td>
<td>VDPScreenCapture_Interface</td>
<td>v1</td>
<td>vdpScreenCapture.h</td>
</tr>
<tr>
<td>GUID_VDPScreenCapture_Interface_V2</td>
<td>VDPScreenCapture_Interface</td>
<td>v1</td>
<td>vdpScreenCapture.h</td>
</tr>
<tr>
<td>GUID_VDPScreenCapture_Interface_V3</td>
<td>VDPScreenCapture_Interface</td>
<td>v1</td>
<td>vdpScreenCapture.h</td>
</tr>
<tr>
<td>GUID_VDPScreenCapture_Interface_V4</td>
<td>VDPScreenCapture_Interface</td>
<td>v1</td>
<td>vdpScreenCapture.h</td>
</tr>
</tbody>
</table>

#### Sample Code

The following sample code shows how to request an interface.
```
VDP_SERVICE_QUERY_INTERFACE qi; VDPService_ChannelInterface ci;
qi.QueryInterface(&GUID_VDPService_ChannelInterface_V1, &ci);
```

### Application

The user launches the application, which is the component that runs on the remote desktop. 

After the Application starts and `vdpService.dll` is loaded, the application calls `VDPService_ServerInit()`. When the application exits, it must call `VDPService_ServerExit()`.

#### Horizon Session Enhancement Server Functions

The following table describes the server functions.

<table>
<thead>
<tr>
<th>Function</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>VDPService_ServerInit</td>
<td>The application calls this function when it starts. It must pass an identifying string (the token) to the function. The function returns a pointer to <code>VDP_SERVICE_QUERY_INTERFACE</code> and the channel handle for this application, which uses the channel handle to initialize user threads.</td>
</tr>
<tr>
<td>VDPService_ServerExit</td>
<td>The application calls this function when it closes down.</td>
</tr>
<tr>
<td>VDPService_Serverinit2</td>
<td>Same as <code>VDPService_ServerInit</code> but for a different session. Caller needs to have sufficient privilege.</td>
</tr>
<tr>
<td>VDPService_ServerExit2</td>
<td>Same as <code>VDPService_ServerExit</code> but for a different session. Caller needs to have sufficient privilege.</td>
</tr>
</tbody>
</table>

#### Sample Code

The following sample code shows how an application initializes.
```
/* program startup (_tWinMain for example) */
VDP_SERVICE_QUERY_INTERFACE qi; 
void *channelHandle;
VDPRPC_VariantInterface vi;
VDPOverlay_GuestInterface ogi;
/* other interfaces omitted */
VDPService_ServerInit("example" /* token */, &qi, &channelHandle); 
qi.QueryInterface(&GUID_VDPRPC_VariantInterface_V1, &vi); 
qi.QueryInterface(&GUID_VDPOverlay_GuestInterface_V1, &ogi);
/* ... */
```

### Plug-in

The main difference between the plug-in and the application is that the Horizon software loads the code on the client. Therefore, the user-compiled code must be in a DLL or a shared object that the system loads. 

The plug-in must export the functions described in the following table.

#### Horizon Session Enhancement Exported Plug-In Functions

<table>
<thead>
<tr>
<th>Function</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>VDPService_PluginInit</td>
<td>Invoked when the DLL or SO is loaded. The plug-in receives its reference to <code>VDP_SERVICE_QUERY_INTERFACE</code>.</td>
</tr>
<tr>
<td>VDPService_PluginInitWithPath</td>
<td>Similar to the <code>VDPService_PluginInit function</code>, but with an additional parameter for the absolute path to where the plug-in was loaded from the disk.</td>
</tr>
<tr>
<td>VDPService_PluginExit</td>
<td>Invoked when the library is unloaded and the user session ends.</td>
</tr>
<tr>
<td>VDPService_PluginGetTokenName</td>
<td>Horizon Session Management uses this function to match the plug-in with the application. The token that this function returns must match the token that the matching application passes to <code>VDPService_ServerInit</code> for communication to occur.</td>
</tr>
<tr>
<td>VDPService_PluginCreateInstance</td>
<td>Invoked when a new channel's identifier matches the one that 
<code>VDPService_PlugingetTokenName</code> returns. More than one instance of a plug-in may exist. Horizon Session management matches instances of the plug-in to the correct channel.</td>
</tr>
<tr>
<td>VDPService_PluginDestroyInstance</td>
<td>Invoked when a new channel's identifier matches the one that 
<code>Called when the channel this plug-in instance runs on closes.</td>
</tr>
</tbody>
</table>

## RPC API

With the RPC API, applications and plug-ins can communicate using virtualacross channels. You must perform all VDPService initialization steps before you call the RPC API.

### Channel Object

Before communication can occur, a channel object with the same name must exist on both sides of the connection. To create a channel object, call the `v1.CreateChannelObject` method. It does not matter whether the channel object is created in the application or in the plug-in first. The initial state of the channel object is disconnected.

When a channel object is created, a message is sent to the other side of the connection, where the callback function `v1.OnPeerObjectCreated` is called. To create a matching object, call the `v1.CreateChannelObject` method. After the matching object is created, the state of the object on both sides is connected and both sides receive a state change notification.

After a channel object is connected, you can request a side channel for this object. There are two types of side channels: virtual side channel and TCP side channel. A virtual side channel is an additional virtual channel. A TCP side channel is a TCP socket connection between a client and an agent. When a side channel is established and both sides receive a state change notification, the state of the channel object will change to VDP_RPC_OBJ_SIDE_CHANNEL_CONNECTED.

For a TCP side channel, an agent application can switch to stream data mode to save resources. In stream data mode, all VDPService internal threads will be exited and an application has to use a TCP socket to send data to and receive data from a plug-in. RPC packets can be created and parsed by stream data APIs.

### Invoke

After you create a channel object, you can invoke an RPC with the `v1.Invoke` method. You must make the v1.Invoke call on the thread that you create the object on, unless the object is configured to allow invoke on any thread.

The `v1.Invoke` call requires a ChannelContext data structure, which is a wrapper for all the data for the RPC, such as the command, parameters, and so on. You create a context with the `v1.CreateContext` function. After the context is created, add information for the RPC to the context with the `VDPRPC_ChannelContextInterface` methods and pass the context to `v1.Invoke`. Even though you create the context, if the call to `Invoke` succeeds, the API is responsible for freeing the context. This is because of the asynchronous nature of the API. When the call to `v1.Invoke` returns, the context might still be in use. If the call to Invoke fails, you are responsible for freeing the context using `v1.DestroyContext`.

Each channel context has a unique ID that you can retrieve with the `v1.GetId` method. The ID of a context that is passed to a `v1.Invoke` call is returned as the `contextId` parameter to the `v1.OnDone` and `v1.OnAbort` handlers. You can use the contextId to map the callbacks to the original `v1.Invoke` call. The ID of a context (e.g. the one returned from `context.v1.GetId`) that is passed to the `v1.OnDone` and `v1.OnAbort` handlers represents the context ID from the other side of the connection this is why the originating context ID is passed in as a separate parameter.

### Variant

All data that you add to a channel context must be in a VDP_RPC_VARIANT data structure. The following code sample shows how to add data to a variant and append it to a context.

```
VDP_RPC_VARIANT var;
VDPRPC_VariantInterface varIface;
VDPRPC_ChannelContextInterface ctxtIface; 
void *contextHandle;

// Call VariantInit() before using the variant
// Failure to call VariantInit() can cause memory corruption issues 
varIface.v1.VariantInit(&var);

// Add the parameters to the context 
varIface.v1.VariantFromInt32(&var, 32); 
ctxtIface.v1.AppendParam(contextHandle, &var);

// The same variant can be used for multiple parameters 
varIface.v1.VariantFromString(&var, "sample string"); 
ctxtIface.v1.AppendNamedParam(contextHandle, "sample param", &var);

// Call VariantClear() after all parameters are added to the context
// Failure to call VariantClear() can lead to memory leaks 
varIface.v1.VariantClear(&var);  
```

It is recommended that you use the `RPCVariant` class included with the sample code.

You must call `v1.VariantInit` before using a variant to avoid causing memory corruption and you must call `v1.VariantClear` method when you are done with the variant to ensure that all resources are freed.

It is recommended that you use the RPCVariant C++ class included with the sample code which will automatically call `v1.VariantInit` and `v1.VariantClear` for you.

```
RPCPluginInstance* plugin; 
VDPRPC_VariantInterface varIface; 
VDPRPC_ChannelContextInterface ctxtIface; 
void *contextHandle;

RPCVariant var(plugin); 

// Add the parameters to the context 
varIface.v1.VariantFromInt32(&var, 32); 
ctxtIface.v1.AppendParam(contextHandle, &var); 

// The same variant can be used for multiple parameters 
varIface.v1.VariantFromString(&var, "sample string"); 
ctxtIface.v1.AppendNamedParam(contextHandle, "sample param", &var); 
```

### OnInvoke

On a successful `v1.Invoke` call, the peer object receives an `v1.OnInvoke` callback. In this callback you receive a channel context. The context contains all of the information for the call. To respond, add the appropriate return code and return values to the channel context, which is returned to the caller when the `v1.OnInvoke` call returns.

### Application Shutdown

The application must call `VDPService_ServerExit`.

### Plug-In Shutdown

The following functions are called during the plug-in shutdown process.

- `VDPService_PluginDestroyInstance` is called when the channel associated with the remote desktop application is closed. Each call to `VDPService_PluginCreateInstance` has a corresponding call to `VDPService_PluginDestroyInstance`.

- `VDPService_PluginExit` is called when the Horizon session ends, immediately before the plugin DLL is unloaded. The plug-in must free all resources and shut down.

## Overlay API

With the Overlay API, you can overlay a window or an image on top of another window or image. You typically do this to make video that is playing on the local client appear as if it is playing in a window on the remote desktop.

### Guest Setup

To use the Overlay API, the first step is to initialize the guest interface by calling the `v1.Init` method. After a successful initialization, register the window that you want to overlay by calling the `v1.RegisterWindow` or `v3.RegisterWindow` method. The size and position of the registered window are tracked and sent to the client automatically. If the client does not reject the registered window, you receive the `v1.OnOverlayReady` callback. When you receive this callback, you call the `v1.EnableOverlay` function to display the overlay on the client.

When you are finished with the window, unregister it by calling `v1.UnregisterWindow`.

### Client Setup

On the client, the first step is to initialize the interface by calling `v1.Init`, which returns a context ID. You use the ID to identify the plug-in instance. When the guest registers a window, the client is notified through the `v1.OnWindowRegistered` sink callback, which gives you a window ID. You need both the context ID and the window ID to update the overlay.

After you receive the `v1.OnOverlayReady` callback, you can start displaying your image by calling the `v1.Update` or `v2.Update` method. The API does not keep a copy of the image unless the `copyImage` flag is set to true. If you do not own the image resource or you need to free it, you must set the `copyImage` flag.

When you are finished with the overlay, call the `v1.Exit` method.

## Screen Capture API

The VDPScreenCapture API is called from your Session Enhancement SDK plugin that runs on the Horizon Client and allows you to query information about the topology of the remote desktop as well as capture images of the remote desktop. 

### Screen Capture

Use the Screen Capture functions capture an image of the entire remote desktop or a specified area of the remote desktop. 

### Read Back Window

The Read Back Window functions allow you to track a window associated with a specific process on the remote desktop. You can get notifications when it resizes, moves, or updates. You can also capture the image of the window. These functions are only supported by the Blast protocol and are dependent on the version of both the Horizon Client and Horizon Agent. 

## Virtual Channel and Side Channel Security

This section describes the security features of virtual channels and side channels which run over Horizon session connections.

### Virtual Channel Security

Virtual channels run over the session connection that is established by the remote protocol and rely on security offered by the protocol. The communication over these supported protocols is highly secure and based on industry-recommended security practices. The endpoints negotiate the actual session encryption algorithm that is used by the selected protocol.

In addition, you can increase the security of virtual channels by configuring a list of allowed channels. This configuration allows only the channels in the list to be opened by legitimate requests and prevents all other channels from being opened. To create the allow list, add the channels as registry entries to the .reg file included with the SDK. For more information, see Omnissa Knowledge Base (KB) [article 84156](https://kb.omnissa.com/s/article/84156).

For detailed information about the types of security offered by the supported protocols, see [Understanding Client Connections](https://docs.omnissa.com/bundle/HorizonOverviewDeployment/page/UnderstandingClientConnections.html).

To configure the cipher suites and protocols used by the client, follow the client-specific procedure described in [Configuring Security Protocols and Cipher Suites for Specific Client Types](https://docs.omnissa.com/bundle/Horizon-Security/page/ConfiguringSecurityProtocolsandCipherSuitesforSpecificClientTypes.html).

For information about the security features of Horizon Cloud Service next-gen, see the Horizon Cloud Service -- next-gen Security Overview [technical article](https://techzone.omnissa.com/resource/horizon-cloud-service-%E2%80%93-next-gen-security-overview).

### Side Channel Security

Side channels rely on the Advanced Encryption Standard (AES) 128-cipher algorithm in Cipher Block Chaining (CBC) mode. The algorithm uses an explicit initialization Vector (IV) as a confidentiality mechanism within the context of the IPsec. The random number is generated on the remote desktop and exchanged through the main virtual channel which is secured by the protocol's security layer. This exchange does not require any negotiation for an SSL/TLS handshake. The application using the side channel must opt in to use the encryption.

The following API methods provide the implementation details for the encryption:

- `v1.CreateChannelObject()`: Use config flags to negotiate the encryption support between sender and receiver. 

- `v3.GetObjectOptions()`: Use this function to verify whether both the sender and receiver support encryption.

`v3.CreateContext()`: Use this function to create the encryption context before send and invoke events.

## Installation

To use the Horizon Session Enhancement API, you must use `vdpService.dll`, which is installed by the Horizon agent software.

### Remote Desktop

The file `vdpService.dll` must exist on the remote desktop. When you install the Horizon agent software, this file is automatically installed on the remote desktop. For the location of the installation directory, see the applicable registry:

- Agent versions 2412 and later - `HKLM\Software\Omnissa\Horizon\RemoteExperienceAgent\InstallPath`

- Agent versions 2406 and earlier - `HKLM\Software\****** Inc.\****** VDM\RemoteExperienceAgent\InstallPath`

The 64-bit version of `vdpService.dll` is installed under `x64` in the same directory.

To load `vdpService.dll`, use the code in `vdpService_import.cpp` which is included with the SDK.

### Client

The file `vdpService.dll` (.so, .dylib) already exists on the client system and is loaded by Horizon Client. Your plugin must not load `vdpService.dll`, because loading extra copies can cause problems.

#### Windows Client

Register the vdpService plugin to the applicable registry location:

- Client versions 2412 and later - `HKLM\Software\Omnissa\Horizon\VDPService\Plugins`
- Client versions 2406 and earlier - `HKLM\Software\****** Inc.\****** VDPService\Plugins`
- Use the function `VDPService_RegisterPlugin` which is included in the SDK to register your plugin. There is also a matching function to unregister the plugin `VDPService_UnRegisterPlugin` (see `helpers.cpp/.h`).

#### Linux Client

Copy the vdpService plugin to the applicable location: 

- Client versions 2412 and later - `/lib/.omnissa/vdpService` or `~/.omnissa/vdpService`
- Client versions 2406 and earlier - `/lib/.*****/vdpService` or `~/.*****/vdpService`
- The Makefile that comes with the samples shows how to copy the .so library to the correct folder. 

Make sure that the plug-ins have the execute permission.

#### Mac Client

Copy the vdpService plugin to the applicable location: 
- Client versions 2412 and later - `/Library/.omnissa/vdpService` or `~/.omnissa/vdpService`
- Client versions 2406 and earlier - `/Library/.*****/vdpService` or `~/.*****/vdpService`
- The Makefile that comes with the samples shows how to copy the .dylib library to the correct folder
  
Make sure that the plug-ins have the execute permission. The plugin must be signed with your Apple developer's ID certificate unless SIP is disabled.

## Sample Program Code

The Horizon Session Enhancement SDK includes a directory called samples that contains examples of how to use the API.



