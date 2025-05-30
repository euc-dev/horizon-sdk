---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Installation and Configuration for browser-based WebRTC application

This section describes the SDK installation and setup procedures for browser-based WebRTC application

## System Requirements

**Omnissa Horizon Client Version**
- Minimum required version: 8.15.0 (Horizon 2503) for both agent and client<br>To support the latest features and interfaces of the SDK, ensure that you are running the latest release version of Horizon 8, which is available through [Omnissa Customer Connect](https://customerconnect.omnissa.com/downloads/info/slug/desktop_end_user_computing/omnissa_horizon_clients/8).
- Omnissa Horizon Cloud Service on Microsoft Azure<br>To support the latest features and interfaces of the SDK, ensure that your Horizon Cloud pods are running the latest release version of the pod manifest.
**Note**: If you are running an earlier release version of Horizon 8 or of the Horizon Cloud Service on Microsoft Azure pod manifest, some features and interfaces of the Horizon SDK for WebRTC Redirection are not supported.

Horizon 2503 release is the first release to support call reconnection (ICE restart) functionality. Earlier versions do not support this feature.

**Client System**<br>
The SDK only supports Windows client endpoints at this time. Verify that each client system meets the following requirements:<br>
- Windows 11 or Windows 10<br>
- 2.4 GHz dual-core processor (minimum)<br>
- Horizon Client for Windows 2503 or later

**Note:** For information about the operating systems supported for a specific version of Horizon Client, see the release notes for that client version.

**Remote Desktop**<br>
Verify that the source virtual machine for each remote desktop meets the following requirements:
- Equipped with 2 vCPUs, at minimum<br>
- Running one of the following operating systems:<br>
  - Windows 11, Windows 10<br>
  - Windows 10 Enterprise (multi-session, for Azure only)<br>
  - Windows Server 2019, 2016, 2012 R2<br>

**UC Application**<br>
The Horizon SDK for WebRTC Redirection supports UC applications built on the Electron software framework.

**Note:** The SDK for browser-based WebRTC application only supports UC applications running on Omnissa VDI deployments. It does not support CEF, PWA.
