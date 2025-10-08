---
layout: page
title: newMediaStream(tracks)
hide:
  #- navigation
  - toc
---

Creates a new `MediaStream` object for the application.  
This is similar to the [`MediaStream` constructor](https://developer.mozilla.org/en-US/docs/Web/API/MediaStream/MediaStream).

### Parameters

| Name    | Description |
|---------|-------------|
| `tracks` | *(Required)* Array of `MediaStreamTrack` objects created or returned by the SDK |

### Return Values
| Type        | Description           |
|-------------|-----------------------|
| `MediaStream` | A new `MediaStream` object |

### Code Example
```js
let _stream = await HorizonWebRtcRedirectionAPI.newMediaStream(_tracks);
```


