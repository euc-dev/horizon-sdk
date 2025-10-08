---
layout: page
title: getCallConfig(index)
hide:
  #- navigation
  - toc
---

Helper function that processes call configurations and returns the associated `pcfId`.

Use this to retrieve configuration data when handling multiple call sessions or scenarios indexed by ID.

### Parameters

| Name    | Type    | Description                         |
|---------|---------|-------------------------------------|
| `index` | Number  | Index of the call configuration to retrieve |

### Return Values

| Type   | Description         |
|--------|---------------------|
| Object | Object containing the `pcfId` field |

### Code Example
```js
let config = HorizonWebRtcRedirectionAPI.getCallConfig(0);
console.log(config.pcfId);
```

