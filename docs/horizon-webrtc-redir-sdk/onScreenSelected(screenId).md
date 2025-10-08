---
layout: page
title: onScreenSelected(screenId)
hide:
  #- navigation
  - toc
---

Selects the preferred monitor to use for screen sharing.

### Parameters

| Name       | Description |
|------------|-------------|
| `screenId` | *(Required)* ID returned from `getScreenInfo()` |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.onScreenSelected("monitor01");
```


