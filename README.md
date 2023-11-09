# Network-Port-Scanner
import socket
import threading

# Define the target IP address
target = "192.168.1.1"

# Define the port range to scan
ports = range(1, 65535)

# Create a socket object
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the scan function
def scan_port(port):
   try:
       sock.connect((target, port))
       print(f"Port {port} is open")
   except:
       pass

# Create a thread for each port
threads = []
for port in ports:
   t = threading.Thread(target=scan_port, args=(port,))
   threads.append(t)

# Start the threads
for t in threads:
   t.start()

# Wait for the threads to finish
for t in threads:
   t.join()
