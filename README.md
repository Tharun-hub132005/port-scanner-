## Port Scanner Using Pytho ##
# Requirements:
 *  Python
 * socket and threading modules
*  Command-line interface
# Ethical Hacking: 
Using tools like port scanners requires permission from the network owner. Unauthorized scanning can be illegal and unethical. This script is for educational purposes and responsible use only.

# Basic Assessment:
This script provides a very basic level of assessment. True vulnerability assessment involves much more sophisticated tools and methodologies (e.g., vulnerability scanners like Nessus, OpenVAS, Metasploit, etc.).

# Firewalls and IDS/IPS:
Modern networks often have firewalls and Intrusion Detection/Prevention Systems (IDS/IPS) that can detect and block port scans. Be aware that your scans might be detected and potentially trigger alerts.

# Performance and Threading: 
While threading helps, scanning a large range of ports on many hosts can still be time-consuming. 
# How to Use the Script:

* Save:Save the code as a Python file (e.g., port_scanner.py).

* Open Terminal/Command Prompt: Navigate to the directory where you saved the file.
* Run: Scan a specific IP with default common ports (recommended for quick checks):
* Bash

python port_scanner.py your_target_ip_or_hostname -c
# Scan a specific IP for a single port:

* Bash

python port_scanner.py your_target_ip -p 22
# Scan a specific IP for a list of ports:

 * Bash

python port_scanner.py your_target_ip -p 21,22,80,443
# Scan a specific IP for a range of ports:

* Bash

python port_scanner.py your_target_ip -p 1-1024
# Scan with a custom timeout:

* Bash

python port_scanner.py your_target_ip -p 1-100 -t 0.5
# Scan a hostname:

# Explanation of the Code:
* socket Module:

 * socket.socket(socket.AF_INET, socket.SOCK_STREAM): Creates a new socket object. AF_INET specifies IPv4, SOCK_STREAM specifies TCP (for reliable, connection-oriented communication, which ports typically use).

* sock.settimeout(self.timeout): Sets a timeout for the connection attempt. If a connection isn't established within this time, it fails. This is crucial for avoiding indefinite hangs on unresponsive ports.

* sock.connect_ex((self.target_ip, port)): Attempts to connect to the target IP and port. connect_ex returns 0 if the connection is successful (port is open) and an error code otherwise (e.g., 10061 for "Connection refused" which means the port is likely closed, or 10060 for "Connection timed out" which means no response).

* sock.close(): Closes the socket.

* socket.gethostbyname(target): Resolves a hostname to an IPv4 address.

* socket.gethostbyaddr(ip_address): Attempts to resolve an IP address to a hostname (reverse DNS lookup).

# threading Module:

* threading.Thread(target=self.scan_port, args=(port,)): Creates a new thread. target is the function the thread will run, and args are the arguments passed to that function.

* thread.start(): Starts the thread, making it run concurrently.

* thread.join(): Waits for the thread to complete its execution before the main program continues. This ensures all scan results are collected.

* threading.Lock(): Used to create a lock. When multiple threads try to modify a shared resource (like self.open_ports), a lock prevents race conditions (where threads interfere with each other, leading to incorrect data). with self.lock: ensures the lock is acquired before appending and released automatically afterward.

# argparse Module:

* Provides a convenient way to parse command-line arguments.

* parser.add_argument(...): Defines the expected arguments (e.g., target, -p, -t).

* args = parser.parse_args(): Parses the arguments provided by the user.

# COMMON_PORTS Dictionary:

A simple dictionary mapping well-known port numbers to their common service names. This enhances the readability of the scan results.

# Basic Vulnerability Assessment Clues:

* The report_results method includes a section that provides some initial clues about what open ports might imply from a security perspective. This is where the "basic vulnerability assessment" part comes in, by guiding the user on what to look for next.Bash

python port_scanner.py example.com -c



