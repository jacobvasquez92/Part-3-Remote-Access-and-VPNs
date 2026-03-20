# Part 3: Remote Access and VPNs  
By Jacob Vasquez  

This plan addresses the security requirements for the implementation of a remote workforce by focusing on three core directives: establishing secure remote access to the internal network, implementing controls for preventing unauthorized access, and protecting all information transmitted between remote users and organizational servers from snooping. The deployment of a Virtual Private Network (VPN), specifically an SSL/TLS VPN, is the solution chosen to create a secure, encrypted transmission channel, balancing high security with operational flexibility and user-friendly experience.  

### Challenges of a Remote Workforce  

Fundamental security issues introduced by a remote workforce are increased attack surface and the breakdown of the standard network perimeter.  The risk of successful phishing attacks has increased among remote workers because an "at home" environment often leads to distractions, making them more likely to click on suspicious links (Pratt, 2025).  Remote workers’ local machines and accompanying software may be unsecure and vulnerable.  With an increase in Bring Your Own Device (BYOD) policies, it becomes more difficult to confirm secure devices and if remote workers are adhering to security policies.  

Typically, remote workers rely on residential Internet Service Providers (ISPs) and network devices that may interfere with corporate connectivity.  Additional risks are at-home Wi-Fi and endpoint passwords that can be weak, and devices potentially in need of patching and updates.  An unsecure local host is susceptible to intrusion and can lead to a compromise of the corporate network.  

The decision to implement a remote workforce at its core depends on the ability of a network architecture to create a secure transmission that ideally protects confidentiality, integrity, and availability.  Compromise in any of these factors comes at the heels of a risk management analysis and risk the organization is willing tolerate.  

The solution to connecting a dispersed remote workforce comes by way of a Virtual Private Network (VPN).  VPNs come in many forms, satisfying various organizational demands.  The VPN deployment options that were considered to try and satisfy the directives of this plan were Internet Protocol Security (IPsec) and Secure Socket Layer/Transport Layer Security (SSL/TLS).  Both structures provide data confidentiality through strong cryptographic encryption and key exchange architecture. Therefore, the selection will come down to operational efficiency, noting performance and complexity, and preventing unauthorized access through granular access control mechanisms.  

# Operating in the OSI Model  

IPsec VPN and SSL/TLS VPN operate at different layers of the Open Systems Interconnection (OSI) Model, IPsec at Layer 3 (Network) and SSL/TLS at Layer 4 (Transport) and Layer 7 (Application).  Operating at different layers has profound network implications.  

Operating at Layer 3 gives IPsec the ability to secure all traffic between endpoints regardless of the application being used. Comprehensive network-wide encryption is the benefit of sitting above the IP layer.  

SSL/TLS operates at Layer 4 and Layer 7, primarily sitting at Layer 7.  Operating at Layer 7 allows the use of widely accepted TLS protocol to create secure encrypted tunnels.  Adaptable to remote workers, web specific application sessions are secured allowing access to corporate resources from a user’s standard web browser.  


