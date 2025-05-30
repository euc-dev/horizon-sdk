---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# Channel Interaction Functions

The Horizon Session Enhancement SDK contains the header file `vdpService_interfaces.h`. This file declares two structures of function pointers: `VDPService_ChannelInterface` and `VDPService_ObserverInterface`.

You can use the VDPService_ChannelInterface APIs to interact with the remote connection or channel. With `VDPService_ObserverInterface`, two components within the same process can communicate with each other.

`VDPService_ChannelInterface` consists of the following functions:

- [`v1.Broadcast`](v1.Broadcast.md)
- [`v1.Connect`](v1.Connect.md) 
- [`v1.Disconnect`](v1.Disconnect.md)
- [`v1.GetChannelState`](v1.GetChannelState.md)
- [`v1.GetConnectionState`](v1.GetConnectionState.md)
- [`v1.Poll`](v1.Poll.md)
- [`v1.RegisterChannelNotifySink`](v1.RegisterChannelNotifySink.md)
- [`v1.RegisterObserver`](v1.RegisterObserver.md)
- [`v1.ThreadInitialize`](v1.ThreadInitialize.md)
- [`v1.ThreadUninitialize`](v1.ThreadUninitialize.md)
- [`v1.UnregisterChannelNotifySink`](v1.UnregisterChannelNotifySink.md)
- [`v1.UnregisterObserver`](v1.UnregisterObserver.md)
- [`v2.GetSessionType`](v2.GetSessionType.md) 
- [`v2.SwitchToStreamdataMode`](v2.SwitchToStreamDataMode.md)
- [`v3.Poll`](v3.Poll.md)

`VDPService_ObserverInterface` consists of the following functions:

- [`v1.Broadcast`](v1.Broadcast.md)
- [`v1.RegisterObserver`](v1.RegisterObserver.md) 
- [`v1.UnregisterObserver`](v1.UnregisterObserver.md)

