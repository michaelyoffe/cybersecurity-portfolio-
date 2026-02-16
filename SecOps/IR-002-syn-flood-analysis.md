# Cybersecurity Incident Report: Network Interruption Analysis

## Section 1: Identify the type of attack that may have caused this network interruption

| Category | Analysis |
| :--- | :--- |
| **Attack Identification** | One potential explanation for the website's connection timeout error message is that a malicious actor used a DoS attack. The logs show that the packets are being sent using the TCP protocol and the server being flooded with SYN packets, indicating this is a SYN flood attack. |
| **Impact on Organization** | When this attack is used, it floods the server causing a time out in the company website. This can be damaging to the organization from the unavailability of the website causing service outage. The down time can cause revenue loss and reputation damage. |
| **Future Prevention** | Using tools such as firewalls and DDoS protection services can prevent this attack in the future. |

---

## Section 2: Explain how the attack is causing the website to malfunction

| Phase | Technical Explanation |
| :--- | :--- |
| **Step 1: SYN** | The client sends a SYN packet to the server to start a connection and request synchronization of sequence numbers. |
| **Step 2: SYN-ACK** | The server responds with a SYN-ACK packet, acknowledging the client’s request and sending its own sequence number. |
| **Step 3: ACK** | The client sends back an ACK packet to confirm it received the server’s response. At this point, the connection is established and data transfer can begin. |
| **Attack Analysis** | In this case of SYN attack, a malicious actor sends a large number of SYN packets all at once, overwhelming the server causing users to see timeouts, connection errors, or very slow responses. When this happens, there are no server resources left for legitimate TCP connection requests. |
| **Evidence in Logs** | The logs indicate a large number of SYN requests from many IP addresses, missing ACK responses and many connections stuck in the half open state. This affects the server by not allowing real users to connect. |



---
