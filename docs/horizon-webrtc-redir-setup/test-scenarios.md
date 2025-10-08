---
layout: page
title: Test Scenarios
hide:
  #- navigation
  - toc
---

Omnissa recommends running the following test scenarios to verify that your UC application works as expected with Media Optimization enabled through the Horizon SDK for WebRTC Redirection.

> **Note:** Scenario 12 tests fallback behavior when the client does not support Media Optimization but the remote desktop does. In this case, the app should still function using the Real-Time Audio-Video (RTAV) feature.

| No. | Description                           | Details |
|-----|---------------------------------------|---------|
| 1   | One-to-one (1:1) calls                | Start a person-to-person call with audio. Test across VDI and non-VDI users, including cross-org scenarios. |
| 2   | Group calls                           | Start a group call from a multiperson chat thread (if supported). |
| 3   | Meetings                              | Join a meeting from within the app or calendar invite. Verify functionality with both VDI and non-VDI participants. |
| 4   | Audio-to-video escalation             | During an audio call or meeting, turn on your camera to escalate to video. Test muting/unmuting the camera and verify video transitions. |
| 5   | Screenshare                           | During a 1:1 call or meeting, share your desktop and confirm the receiver sees the shared screen. |
| 6   | Multi-monitor screenshare             | Share screen 1, end it, then share screen 2. Confirm both screens display properly. |
| 7   | In-call device settings               | While in a call or meeting, change your active device (mic, speaker, etc.). Verify the switch works in real time. |
| 8   | Mute/unmute using in-app controls     | Use the app UI to mute/unmute. Verify audio is correctly suppressed and restored. |
| 9   | Escalation from 1:1 to group call     | Add another participant to a 1:1 call and confirm the escalation works. |
|10   | Hold/resume in meetings               | Place a meeting on hold while accepting a 1:1 call. Then resume the meeting and confirm both actions succeed. |
|11   | PSTN calling                          | Initiate a call to a PSTN number or add one to an existing call. Repeat for meetings. |
|12   | Fallback case                         | Disable Media Optimization from Horizon Client settings. Reconnect to a remote desktop with Media Optimization enabled. Verify that the app continues to work using RTAV (non-optimized). |

> For more about fallback and RTAV behavior, see:  
> [System Requirements for Real-Time Audio-Video](https://docs.omnissa.com/bundle/Horizon-Remote-Desktop-FeaturesV2206/page/SystemRequirementsforReal-TimeAudio-Video.html)


