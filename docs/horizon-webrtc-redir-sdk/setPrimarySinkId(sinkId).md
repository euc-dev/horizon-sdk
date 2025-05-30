---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# `setPrimarySinkId(sinkId)`

Sets the default output device for audio playback on the client.

### Parameters

| Name     | Description |
|----------|-------------|
| `sinkId` | *(Required)* The ID of the audio output device |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.setPrimarySinkId("audioDevice01");
```

