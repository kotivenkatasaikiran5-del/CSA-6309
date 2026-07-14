with open("ioc_list.txt", "w") as f:
    f.write("45.33.32.156\n")
    f.write("198.51.100.23\n")
    f.write("203.0.113.99\n")

with open("sample_traffic.log", "w") as f:
    f.write("2026-07-08 10:01:12 connection from 10.0.0.5\n")
    f.write("2026-07-08 10:02:44 connection from 45.33.32.156\n")
    f.write("2026-07-08 10:03:10 connection from 192.168.1.20\n")
    f.write("2026-07-08 10:04:55 connection from 203.0.113.99\n")

def load_iocs(filename):
    with open(filename, "r") as file:
        return set(line.strip() for line in file if line.strip())

def scan_log(logfile, iocs):
    with open(logfile, "r") as file:
        for line in file:
            for ip in iocs:
                if ip in line:
                    print("ALERT: Known malicious IP found ->", line.strip())

iocs = load_iocs("ioc_list.txt")

print("=" * 60)
print("     INDICATOR OF COMPROMISE (IoC) MATCHING")
print("=" * 60)

print(f"Loaded {len(iocs)} IoCs\n")

scan_log("sample_traffic.log", iocs)

print("\nScan Complete!")  
<img width="943" height="697" alt="WhatsApp Image 2026-07-14 at 11 32 27 AM" src="https://github.com/user-attachments/assets/9add9a1b-a71c-4346-b482-d78d14fdb57b" />
