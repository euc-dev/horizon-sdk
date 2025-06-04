# `setSinkId(id, sinkId)`

Sets the audio output device for a specific sound stream (e.g., a ringtone or alert).

### Parameters

| Name   | Description |
|--------|-------------|
| `id`   | *(Required)* Audio stream or ringtone identifier |
| `sinkId` | *(Required)* Output device ID |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.setSinkId("audio01", "audioDevice01");
```


