# Infrastructure WIP
The Lab Builder. Serve for all environement setup, diagrams, and Docker/VM madness.

---
# LIMINALSEC TEMPLATE PACK
Because why reinvent the wheel when you can just fork it, break it, and log the errors?
---

## 📁 `README.md` (Generic)
```markdown
# Project Name

## Overview
A short description of what this project does and who it's for.

## Features
- 🔧 What tools/skills are being used?
- 🧪 What does the environment do?
- 🧠 What did you learn or hope to learn?

## Setup
```bash
# Clone the repo
git clone https://github.com/LiminalSec/your-repo-name.git
cd your-repo-name
# Run setup script or docker-compose
```

## Usage
Steps to use the project, including screenshots, sample output, etc.

## File Structure
```plaintext
root-directory/
├── config/
├── scripts/
├── writeups/
├── README.md
```

## Notes
Any caveats, known issues, or weird behavior.

## License
MIT or GPL or "Please don't use this for evil. Or do. I'm not your mom."
```

## 🐳 `docker-compose.yml` (For Hosting a Vulnerable Web App)
```yaml
version: '3'
services:
  dvwa:
    image: vulnerables/web-dvwa
    ports:
      - "80:80"
    restart: unless-stopped
    environment:
      - MYSQL_USER=dvwa
      - MYSQL_PASSWORD=p@ssw0rd
      - MYSQL_ROOT_PASSWORD=root
```

## 🐍 `nmap-automation.py`
```python
import nmap
import sys

scanner = nmap.PortScanner()

def scan_target(target):
    print(f"[+] Scanning {target}...")
    scanner.scan(hosts=target, arguments='-sV -T4')
    for host in scanner.all_hosts():
        print(f"\nHost: {host} ({scanner[host].hostname()})")
        print(f"State: {scanner[host].state()}")
        for proto in scanner[host].all_protocols():
            print(f"Protocol: {proto}")
            ports = scanner[host][proto].keys()
            for port in sorted(ports):
                print(f"Port: {port}\tState: {scanner[host][proto][port]['state']}")

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print("Usage: python nmap-automation.py [target_ip]")
        sys.exit(1)
    scan_target(sys.argv[1])
```

## ✍️ `blog-post-template.md`
```markdown
---
title: "TITLE GOES HERE"
date: YYYY-MM-DD
tags: [tag1, tag2, tag3]
---

## 🧠 TL;DR
One-sentence summary of what this is and why anyone should care.

## 🔍 Background
Explain what you’re testing, studying, or poking with a stick.

## 🛠️ Tools & Setup
List tools used, environments, versions, etc.

## 🕵️ Process / Execution
Detailed steps, screenshots, command outputs, facepalms.

## 💡 Reflections / Lessons Learned
What worked, what didn’t, what cursed knowledge you now possess.

## 📚 References
Links to CVEs, articles, docs, etc.
```

## 📄 `.gitignore` (for Python/Docker projects)
```
__pycache__/
*.pyc
.env
*.log
docker-compose.override.yml
.vscode/
.idea/
```

