---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Mac OS X

1.  Create a configuration file in the appropriate location:

    - Versions 2412 and later -  
        ```
        ~/Library/Preferences/Omnissa Horizon View/config
        ```
    - Versions 2406 and earlier -  
        ```
        ~/Library/Preferences/V***** Horizon View/config
        ```

2.  Add the following at the end of the configuration file.
    ```
    rdpvcbridge.rdpvcbridgeLogger.logLevel=trace
    ```

3.  Restart the Horizon Client.

The log file is located in one of the following locations:

- Versions 2412 and later -  
    ```
    /Users/<USER-NAME>/Library/Logs/Omnissa******-rdpvcbridge-Client-<pid>.log 
    ```
- Versions 2406 and earlier -  
    ```
    /Users/<USER-NAME>/Library/Logs/V*****/******-rdpvcbridge-Client-<pid>.log
    ```