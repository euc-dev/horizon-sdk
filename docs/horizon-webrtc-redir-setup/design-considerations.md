---
layout: page
title: Design Considerations
hide:
  #- navigation
  - toc
---

Omnissa recommends that you consider the following design guidelines when implementing WebRTC media redirection for your UC application in a Horizon environment.

- Configure your application by default to detect whether WebRTC redirection is enabled on the Horizon desktop and if so, to enable WebRTC redirection at the application level. To detect whether WebRTC redirection is enabled on the desktop, have your application check the DWORD value in the registry: 
  `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Omnissa\Horizon\WebRTCRedir\electronAppEnabled`

- Design your application with a setting that allows the administrator to enable and turn off WebRTC redirection at the user level.<br><br>
**Note**: The administrator must have the ability to configure WebRTC redirection at the user level because not all users may be running a client platform supported by the Horizon SDK for WebRTC Redirection. Your application setting should be distinct from the existing WebRTC redirection setting in the Horizon GPO provided by Omnissa.

- To ensure optimal WebRTC performance, set up your application to load the Horizon SDK for WebRTC Redirection only if WebRTC redirection is enabled at the application level. Your application should not load the SDK if WebRTC redirection is not enabled at the application level.

- Have your application fall back to non-VDI behavior when the Horizon Client endpoint does not support WebRTC redirection. In the fallback case, WebRTC media is not redirected but the user can still use your application and access all other functionality within the Horizon desktop. For more information, see scenario 12 under [Test Scenarios](test-scenarios.md) later in this document.

- Design your application with the capability to differentiate between a console session and a Horizon Client remote session. In a console session, WebRTC media should not be redirected but users should still be able to use your application. This capability addresses the case where Horizon Agent is running on a physical machine and users can connect to this machine using either the console or Horizon Client.


