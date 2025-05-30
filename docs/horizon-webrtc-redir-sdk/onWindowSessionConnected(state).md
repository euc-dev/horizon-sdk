---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# `onWindowSessionConnected(state)`

Notifies the SDK about the session’s connection status.

### Parameters

| Name   | Description |
|--------|-------------|
| `state` | *(Required)* Boolean — `true` if connected, `false` if disconnected |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.onWindowSessionConnected(true);
```

