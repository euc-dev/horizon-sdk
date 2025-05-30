---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# `onAudioCreated(audioElem, window)`

Binds an audio element to the SDK for playback redirection on the client.

### Parameters

| Name       | Description |
|------------|-------------|
| `audioElem` | *(Required)* The actual HTML audio element |
| `window`    | *(Optional)* The application window handle (hex string) |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.onAudioCreated(_myAudioElem, "6810070000000000");
```

