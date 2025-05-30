---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# `onVideoCreated(videoElem, window)`

Binds a video element to the SDK for display redirection on the client.

### Parameters

| Name        | Description |
|-------------|-------------|
| `videoElem` | *(Required)* The HTML video element |
| `window`    | *(Optional)* The app window handle (hex string) |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.onVideoCreated(_myVideoElem, "6810070000000000");
```

