---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Debugging and Collecting Logs

RDPVCBridge writes messages to log files to facilitate debugging.

On the agent side, for every application that loads the DLL, a separate log file is created. On the client side, RDPVCBridge creates a single log file for all virtual channel plug-ins. Logging is set to INFO by default and can be changed to ERROR, WARN, INFO, DEBUG, or TRACE. Use the following information to change the logging level.