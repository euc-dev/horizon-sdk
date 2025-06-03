# `playRingtone(id, src, isLoop)`

Plays a ringtone on the client system using a local or remote audio source.

### Parameters

| Name     | Description |
|----------|-------------|
| `id`     | *(Required)* Unique audio identifier |
| `src`    | *(Required)* URL to the ringtone file |
| `isLoop` | *(Required)* `true` to loop the sound; `false` to play once |

### Return Values
None

### Code Example
```js
HorizonWebRtcRedirectionAPI.playRingtone("audio01", "https://example.com/ringtone.mp3", true);
```


