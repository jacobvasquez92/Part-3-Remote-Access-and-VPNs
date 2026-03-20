# Part 3: Remote Access and VPNs  
By Jacob Vasquez  

This plan addresses the security requirements for the implementation of a remote workforce by focusing on three core directives: establishing secure remote access to the internal network, implementing controls for preventing unauthorized access, and protecting all information transmitted between remote users and organizational servers from snooping. The deployment of a Virtual Private Network (VPN), specifically an SSL/TLS VPN, is the solution chosen to create a secure, encrypted transmission channel, balancing high security with operational flexibility and user-friendly experience.  

### Challenges of a Remote Workforce  
---
Fundamental security issues introduced by a remote workforce are increased attack surface and the breakdown of the standard network perimeter.  The risk of successful phishing attacks has increased among remote workers because an "at home" environment often leads to distractions, making them more likely to click on suspicious links (Pratt, 2025).  Remote workers’ local machines and accompanying software may be unsecure and vulnerable.  With an increase in Bring Your Own Device (BYOD) policies, it becomes more difficult to confirm secure devices and if remote workers are adhering to security policies.  

Typically, remote workers rely on residential Internet Service Providers (ISPs) and network devices that may interfere with corporate connectivity.  Additional risks are at-home Wi-Fi and endpoint passwords that can be weak, and devices potentially in need of patching and updates.  An unsecure local host is susceptible to intrusion and can lead to a compromise of the corporate network.  

The decision to implement a remote workforce at its core depends on the ability of a network architecture to create a secure transmission that ideally protects confidentiality, integrity, and availability.  Compromise in any of these factors comes at the heels of a risk management analysis and risk the organization is willing tolerate.  

The solution to connecting a dispersed remote workforce comes by way of a Virtual Private Network (VPN).  VPNs come in many forms, satisfying various organizational demands.  The VPN deployment options that were considered to try and satisfy the directives of this plan were Internet Protocol Security (IPsec) and Secure Socket Layer/Transport Layer Security (SSL/TLS).  Both structures provide data confidentiality through strong cryptographic encryption and key exchange architecture. Therefore, the selection will come down to operational efficiency, noting performance and complexity, and preventing unauthorized access through granular access control mechanisms.  

### Operating in the OSI Model  
---
IPsec VPN and SSL/TLS VPN operate at different layers of the Open Systems Interconnection (OSI) Model, IPsec at Layer 3 (Network) and SSL/TLS at Layer 4 (Transport) and Layer 7 (Application).  Operating at different layers has profound network implications.  

Operating at Layer 3 gives IPsec the ability to secure all traffic between endpoints regardless of the application being used. Comprehensive network-wide encryption is the benefit of sitting above the IP layer.  

SSL/TLS operates at Layer 4 and Layer 7, primarily sitting at Layer 7.  Operating at Layer 7 allows the use of widely accepted TLS protocol to create secure encrypted tunnels.  Adaptable to remote workers, web specific application sessions are secured allowing access to corporate resources from a user’s standard web browser.  

### Fundamental VPN Deployment with Recommendations  
---
*_IPsec:_* IPsec uses Internet Key Exchange (IKE), Encapsulating Security Payload (ESP), and Authentication Header (AH) protocols to establish security associations (SA), creating secure endpoint communications.  These protocols work together to create, at their most secure, a full-tunnel connection that encapsulates a packet in its entirety.  IPsec, fundamentally, provides data confidentiality, integrity, and authentication.  

There are several key drawbacks of IPsec.  First is the operational complexity in configuration and system management.  Dedicated VPN client software needs to be deployed and managed on all user devices, representing a more complex deployment than browser-based SSL/TLS.  Additionally, the use of certificate authentication requires careful certificate management and planning, including generating and signing server certificates, and unique user certificates that must be installed on user devices.  Network Address Translation (NAT) and Port Address Translation (PAT) typically used in residential and public networks conflicts with IPsec protocols and can cause connection failures.  The work around is NAT Traversal (NAT-T) but this adds another layer of complexity to an already complex configuration.  

A fundamental drawback to IPsec implementation is the extensive network access granted to the authenticated user as defined by the tunnel.  This is a function of IPsec operating a Layer 3.  Such access is in full contradiction to this plan’s directives, to the principle of least privilege, and represents an increased attack surface if remote user credentials are compromised.  

-*For these primary reasons, IPsec VPNs are not recommended for deployment.*  

*_SSL/TLS:_* SSL/TLS is a session-based cryptographic protocol operating at the Application Layer designed specifically for web-based applications such as web browsers, email clients, plus numerous other applications.  This is ideal for remote workers needing secure access to corporate web-based applications from any device and any standard web browser.  

Another benefit that can be leveraged is the flexibility of the deployment model.  SSL/TLS can be deployed as a clientless (portal) or client-based (tunnel) VPN.  Clientless deployment eliminates the need for dedicated software, providing access through a web-based portal.  Inherent compatibility is built-in because every modern web browser utilizes SSL/TLS.  This is the most efficient and user-friendly method for corporate access, especially in a Bring Your Own Device (BYOD) environment.  Client-based (tunnel) deployment needs a modest dedicated thin client to provide access to non-web applications and deeper access that provides security beyond the web browser.   Even though there is a need for small client-based software, the inherent firewall traversal benefits of SSL/TLS provide an ease-of-use over IPsec protocols because SSL/TLS utilizes standard HTTP ports (TCP/443).  

SSL/TLS tunneling does come with some maintenance.  When used to fully encapsulate a VPN tunnel, a TCP-over-TCP redundancy can occur leading to packet mishandling and subsequent retransmission delays, degraded performance, and adverse user experience.  To mitigate, full tunnel deployments utilize Datagram Transport Layer Security (DTLS), using SSL/TLS over User Datagram Protocol (UDP).  By avoiding the TCP-over-TCP constraints, SSL/TLS tunneling is competitive with IPsec performance metrics.  

The most beneficial attribute of SSL/TLS VPN is Granular Access Control (GAC).  GAC is based on the principle of least privilege, utilizing Role-Based Access Control (RBAC), Attribute-Based Access Control (ABAC), and Context-Based Access Control (CBAC) limiting user access to session-based applications specific to the services they require.  In effect, all other resources are made invisible.  Unlike IPsec VPNs, SSL/TLS operating at Layer 7 makes it possible for IT Administrators to limit broad network access, protecting against lateral network traversal if user credentials are compromised.  

Based on the information provided, it is recommended to move forward with SSL/TLS VPN to satisfy the onset of a remote workforce.  The ease of large-scale deployment, a user-friendly experience, the flexibility of BYOD deployment, and superior access control make it ideal for Corporation Techs.  

## Additional Considerations:  

Another option to consider is the built-in Microsoft server product Remote Desktop Services (RDS).  RDS can operate as a Remote Desktop Session Host providing pools of desktop sessions and applications for daily use, or as a Remote Desktop Virtualization Host providing personal desktop sessions as virtual machines.  Two important functions of RDS are RD RemoteApp and RD Web Access that help alleviate the need for VPN access for certain scenarios.  Regardless of a user’s OS, RD RemoteAPP allows the user to start a desktop session from their Start Menu as if they are logging on to their local machine.  RD Web Access, in conjunction with RD RemoteApp, can launch in a web browser and access an intranet or be accessed from the internet.  Remote clients have access to internal network resources without the use of a VPN.  

Ideally, RDS turns out to be a viable solution when users need access to specific applications or need full control of a remote machine.  RDS creates a seamless user experience with low overhead, especially for power users needing high computing power.  IT administrators maintain centralized access control over user sessions and permissions while server management is also centralized for maintenance and updates.  






