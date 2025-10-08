---
layout: page
title: getDisplayMedia(constraints)
hide:
  #- navigation
  - toc
---

Captures the contents of the remote desktop as a media stream and returns the stream to the application.  
This function is similar to [`MediaDevices.getDisplayMedia()`](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getDisplayMedia).

### Parameters

| Name        | Description |
|-------------|-------------|
| `constraints` | *(Required)* An object that specifies details about the media stream. [More info](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getDisplayMedia#parameters) |

### Return Values
| Type    | Description |
|---------|-------------|
| Promise | Resolves to a `MediaStream` or rejects with a related `DOMException` |

### Code Example
```js
let _stream = await HorizonWebRtcRedirectionAPI.getDisplayMedia(_constraints);
```


