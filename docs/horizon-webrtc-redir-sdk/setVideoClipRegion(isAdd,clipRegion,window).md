---
layout: page
title: setVideoClipRegion(isAdd, clipRegion, window)
hide:
  #- navigation
  - toc
---

Adds or removes a clipped video display region on the client, associated with a specific application window.

### Parameters

| Name         | Description |
|--------------|-------------|
| `isAdd`      | *(Required)* Boolean — `true` to add a region, `false` to remove |
| `clipRegion` | *(Required)* DOM element (typically a video element) |
| `window`     | *(Optional)* Window handle as a hex string |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.setVideoClipRegion(true, _myVideoElem, "6810070000000000");
```


