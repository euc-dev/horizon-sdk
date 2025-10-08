---
layout: page
title: newPeerConnectionEx(arg1, arg2, callConfig)
hide:
  #- navigation
  - toc
---

Creates a new `RTCPeerConnection` object.  
This is similar to the [`RTCPeerConnection` constructor](https://developer.mozilla.org/en-US/docs/Web/API/RTCPeerConnection/RTCPeerConnection).

### Parameters

| Name           | Description |
|----------------|-------------|
| `configuration` | *(Optional)* Peer connection configuration object (e.g., ICE servers) |
| `callConfig` | *(Optional)* An opaque object specifying the call configuration object. The object can be retrieved through getCallConfig(). If undefined, newPeerConnectionEx() is reduced to newPeerConnection(). |

### Return Values
| Type              | Description           |
|-------------------|-----------------------|
| `RTCPeerConnection` | A new peer connection object |

### Code Example
```js
let callConfig = HorizonWebRtcRedirectionAPI.getCallConfig(configIndex);
let pc = HorizonWebRtcRedirectionAPI.newPeerConnectionEx(_configurations, {}, callConfig);
```


