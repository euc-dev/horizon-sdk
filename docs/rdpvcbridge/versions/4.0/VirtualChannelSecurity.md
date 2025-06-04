# Virtual Channel Security

This topic describes the security features of virtual channels which run over Horizon session connections.

Virtual channels run over the session connection that is established by the remote protocol and rely on security offered by the protocol. The communication over these supported protocols is highly secure and based on industry-recommended security practices. The endpoints negotiate the actual session encryption algorithm that is used by the selected protocol.

In addition, you can increase the security of virtual channels by configuring a list of allowed channels. This configuration allows only the channels in the list to be opened by legitimate requests and prevents all other channels from being opened. To create the allow list, add the channels as registry entries to the .reg file included with the SDK. For more information, see [Omnissa Knowledge Base (KB) article 84156](https://kb.omnissa.com/s/article/84156).

For detailed information about the types of security offered by the supported protocols, see [Understanding Client Connections](https://docs.omnissa.com/bundle/HorizonOverviewDeployment/page/UnderstandingClientConnections.html) in the [Omnissa Documentation](https://docs.omnissa.com/).

To configure the cipher suites and protocols used by the client, follow the client-specific procedure described in [Configuring Security Protocols and Cipher Suites for Specific Client Types](https://docs.omnissa.com/bundle/Horizon-Security/page/ConfiguringSecurityProtocolsandCipherSuitesforSpecificClientTypes.html) in the [Omnissa Documentation](https://docs.omnissa.com/).

For information about the security features of Horizon Cloud Service, see the [Horizon Cloud Service – next-gen Security Overview](https://techzone.omnissa.com/resource/horizon-cloud-service-%E2%80%93-next-gen-security-overview) technical white paper, available from [Omnissa Tech Zone](https://techzone.omnissa.com/).

