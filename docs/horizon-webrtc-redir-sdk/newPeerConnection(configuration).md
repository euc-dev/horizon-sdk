---
layout: page
title: newPeerConnection(configuration)
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

### Return Values
| Type              | Description           |
|-------------------|-----------------------|
| `RTCPeerConnection` | A new peer connection object |

### Code Example
```js
let _pc = HorizonWebRtcRedirectionAPI.newPeerConnection(_configurations);
```
