import re

def check_url(url):
    reasons = []

    if re.match(r"https?://\d{1,3}(\.\d{1,3}){3}", url):
        reasons.append("Uses raw IP address instead of domain name")

    if "@" in url:
        reasons.append("Contains '@' symbol (can hide real destination)")

    if url.count("-") > 3:
        reasons.append("Too many hyphens in domain (common phishing trick)")

    keywords = ["login", "verify", "update", "secure"]
    if any(keyword in url.lower() for keyword in keywords) and not url.startswith("https://"):
        reasons.append("Suspicious keyword without HTTPS")

    return reasons

urls = [
    "https://www.google.com",
    "http://192.168.10.5/login",
    "http://paypal-verify-account.com@evil.com",
    "https://github.com",
    "http://secure-login-update.com",
    "https://amazon.com"
]

print("=" * 60)
print("           PHISHING URL DETECTOR")
print("=" * 60)

for url in urls:
    issues = check_url(url)
    verdict = "SUSPICIOUS" if issues else "Looks OK"

    print(f"\nURL: {url}")
    print(f"Verdict: {verdict}")

    if issues:
        print("Reasons:")
        for reason in issues:
            print(f" - {reason}")

print("\nAnalysis Complete!")
<img width="1332" height="702" alt="poop" src="https://github.com/user-attachments/assets/d54634c8-8300-4439-8722-c8c0058bbb81" />
