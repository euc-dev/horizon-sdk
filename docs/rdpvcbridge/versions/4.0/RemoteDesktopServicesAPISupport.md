---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Remote Desktop Services API Support

RDPVCBridge supports a subset of RDS API functions.

## Client-side API Functions

-  VirtualChannelClose: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelclose](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelclose)

-  VirtualChannelEntry: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelentry](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelentry)

-  VirtualChannelInit: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelinit](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelinit)

-  VirtualChannelInitEvent: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-channel_init_event_fn](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-channel_init_event_fn)

-  VirtualChannelOpen: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelopen](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelopen)

-  VirtualChannelOpenEvent: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nc-cchannel-channel_open_event_fn](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nc-cchannel-channel_open_event_fn)

-  VirtualChannelWrite: [https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelwrite](https://docs.microsoft.com/en-us/windows/win32/api/cchannel/nccchannel-virtualchannelwrite)

## Server-side API Functions

-  GetSystemMetrics (SM_REMOTESESSION): [https://docs.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-getsystemmetrics](https://docs.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-getsystemmetrics)

-  WTSFreeMemory: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsfreememory](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsfreememory)

-  WTSQuerySessionInformationA: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsquerysessioninformationa](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsquerysessioninformationa)

-  WTSQuerySessionInformationW: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsquerysessioninformationw](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsquerysessioninformationw)

-  WTSRegisterSessionNotification: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsregistersessionnotification](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsregistersessionnotification)

-  WTSUnRegisterSessionNotification: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsunregistersessionnotification](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsunregistersessionnotification)

-  WTSVirtualChannelClose: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelclose](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelclose)

-  WTSVirtualChannelOpen: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelopen](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelopen)

-  WTSVirtualChannelOpenEx: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelopenex](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelopenex)

-  WTSVirtualChannelPurgeInput: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelpurgeinput](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelpurgeinput)

-  WTSVirtualChannelPurgeOutput: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelpurgeoutput](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelpurgeoutput)

-  WTSVirtualChannelQuery: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelquery](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelquery)

-  WTSVirtualChannelRead: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelread](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelread)

-  WTSVirtualChannelWrite: [https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelwrite](https://docs.microsoft.com/en-us/windows/win32/api/wtsapi32/nfwtsapi32-wtsvirtualchannelwrite)
