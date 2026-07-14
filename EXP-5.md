import socket

domains = [
    "www.google.com",
    "www.python.org",
    "notarealdomain12345.com"
]

print("=" * 60)
print("        DNS LOOKUP (OSINT BASICS)")
print("=" * 60)

for domain in domains:
    try:
        ip = socket.gethostbyname(domain)
        print(f"{domain:35} -> {ip}")
    except socket.gaierror:
        print(f"{domain:35} -> Could not resolve (invalid/unreachable)")

print("\nDNS Lookup Complete!")
<img width="1357" height="803" alt="000000" src="https://github.com/user-attachments/assets/98857696-e662-464a-9fad-f1ad92da060d" />
