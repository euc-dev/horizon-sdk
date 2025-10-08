---
layout: page
title: onVideoCreated(videoElem, window)
hide:
  #- navigation
  - toc
---

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


