# Linux

1.  Create a configuration file in the appropriate location:

    - Versions 2412 and later -  `~/.omnissa/config`
    - Versions 2406 and earlier -  `~/.v*****/config`

1.  Add the following line at the end of the configuration file.
    ```
    rdpvcbridge.rdpvcbridgeLogger.logLevel=trace
    ```

1.  Restart the Horizon Client.

The log file is located in one of the following locations:

- Versions 2412 and later -  
    ```
    /tmp/omnissa-<USER-NAME>/******-rdpvcbridge-Client-<pid>.log
    ```
- Versions 2406 and earlier -  
    ```
    /tmp/v*****-<USER-NAME>/******-rdpvcbridge-Client-<pid>.log
    ```

