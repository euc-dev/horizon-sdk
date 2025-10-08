---
layout: page
title: onWindowSessionConnected(state)
hide:
  #- navigation
  - toc
---

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


