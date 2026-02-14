# Incident report analysis

## Summary
The organization experienced a Distributed Denial of Service (DDoS) attack that disrupted internal network operations for approximately two hours. The attack was a flood of ICMP packets that caused network services to stop responding and prevented normal internal traffic from accessing network resources. The team responded by blocking all incoming ICMP packets, taking non-critical services offline, and restoring critical network operations.
## Identify
The incident management team audited the company’s network systems, firewall configurations, and access policies to identify the source of the disruption. The audit revealed that a misconfigured firewall allowed incoming ICMP traffic without proper rate limits or source verification. This security gap allowed a malicious actor to flood the network with ICMP packets, resulting in a DDoS attack that temporarily disabled internal network services.
## Protect
The network security team has implemented new policies to prevent future attacks: firewall rule to limit the rate of incoming ICMP packets, source IP address verification on the firewall to check for spoofed IP addresses on incoming ICMP packets, and a Network monitoring software to detect abnormal traffic patterns. Additionally we will implement an IDS/IPS system to filter out some ICMP traffic based on suspicious characteristics.
## Detect
The cybersecurity team will use network monitoring software and an intrusion detection and prevention system (IDS/IPS) to identify unusual ICMP traffic patterns. Firewall logs will be regularly reviewed to catch suspicious or repeated external traffic attempts.
## Respond
During the attack, the cybersecurity team blocked all incoming ICMP packets and shut down non-critical network services to stabilize the system. Critical services were restored as soon as the network became responsive. The incident was documented, and management was informed of the attack and what corrective measures should be taken in the future, such as isolating affected systems to prevent further disruption to the network.
## Recover
The team verified that all network systems and services were fully operational once the attack was mitigated. A post incident review was completed to document lessons learned and improve the organization’s DDoS response plan.
Firewall configurations were updated, and monitoring tools were activated to ensure stability and to block ICMP flood attacks. In the future non-critical network services should be turned off to lower internal traffic. Critical services should be brought back online first. When the ICMP flood ends, all other systems and services can be restored. 

