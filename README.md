# Split-Handshake_Attack_emulator
Script created with the aid of Scapy that simulates the TCP Split-Handshake Attack for educational purposes

The code demonstrates how a client sends a SYN, followed by an anomalous response from the server (which sends a SYN instead of the classic SYN/ACK). The client then responds with a SYN/ACK, and finally, the server completes the handshake with an ACK."

# The Code - Split-Handshake Attack

SYN Sending from the Client
The client constructs an IP/TCP packet with the "S" (SYN) flag and sends it to the server, indicating the start of the connection with a predefined sequence number (1000).

Anomalous Response from the Server
In a typical scenario, the server would respond with a SYN/ACK packet. However, to simulate the TCP Split-Handshake, the "server" (simulated in this case) sends a packet with only the "S" flag and a new sequence number (2000), without the expected acknowledgment.

Client's Response to the Anomalous SYN
Since the client does not recognize the packet as a valid SYN/ACK, it interprets it anomalously and sends a SYN/ACK packet, with an incremented sequence number and an acknowledgment based on the sequence number of the anomalous packet (ack=2001).

Connection Completion
Finally, the server responds with a final ACK, technically completing the three-way handshake, even though in a real scenario, the packet order is ambiguous and potentially exploitable.

This example highlights how manipulating the order and flags in TCP packets can lead to a "split" handshake, altering the normal connection logic.

By using Scapy, we can also analyze in detail how each packet is constructed and transmitted, providing a valuable tool for studying advanced attack and defense techniques in TCP network environments.

⚠️ This software is provided solely for educational and security auditing purposes. It is intended to help network administrators, security professionals, and researchers identify vulnerabilities and improve the security of their own systems.

Unauthorized use of this software on networks or systems without explicit permission from the owner is strictly prohibited. Scanning or probing networks without consent may violate local laws, regulations, and organizational policies. The author and distributor of this software assume no liability for any misuse, legal consequences, or damages resulting from its use.

By using this software, you acknowledge that:

You have obtained explicit authorization to test the target systems.
You take full responsibility for your actions and any consequences arising from them.
You comply with all applicable laws, regulations, and ethical guidelines regarding cybersecurity testing.
If you are unsure about the legality of your actions, do not use this software. Always ensure compliance with ethical hacking standards and responsible disclosure practices.
