---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# `onAudioDisposed(audioElem)`

Cleans up a previously bound audio element when it’s destroyed.

### Parameters

| Name       | Description |
|------------|-------------|
| `audioElem` | *(Required)* The HTML audio element to unbind |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.onAudioDisposed(_myAudioElem);
```

