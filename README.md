# Cybersecurity Portfolio

## About Me

My interest in cybersecurity started when I was a teenager and stumbled across a documentary about hacking and how attackers exploit everyday software. What surprised me most wasn't the technical complexity — it was the mindset: thinking like an adversary, questioning assumptions, and finding the unexpected path. That curiosity never left me.

During my studies I took a network security course that introduced me to penetration testing fundamentals, and from there I began working through online platforms like TryHackMe and PicoCTF. The first time I solved a challenge by chaining together a directory traversal and a weak credential, I was hooked. Cybersecurity felt like the perfect intersection of puzzle-solving, creativity, and real-world impact — a discipline where learning never stops because the threat landscape is always evolving.

---

## CTF Experience Reflection

Participating in Capture the Flag competitions has been one of the most effective ways I've sharpened my technical skills. CTFs compress months of learning into focused, time-boxed sprints where every solved flag feels like a small victory and every unsolved challenge is a lesson.

**What I've learned from CTFs:**

- **Web exploitation** — I've become comfortable identifying and exploiting common web vulnerabilities (SQLi, XSS, IDOR, SSRF) by reading source code, inspecting HTTP traffic with Burp Suite, and reasoning about how server-side logic handles untrusted input.
- **Binary exploitation & reverse engineering** — Working with tools like Ghidra and GDB has taught me how programs behave at the assembly level and where common memory-safety bugs surface.
- **Cryptography** — CTF crypto challenges demystified a lot of the theory I'd studied: I've implemented and broken weak RSA, broken ECB-mode ciphers with block rearrangement, and recovered keys from timing oracles.
- **Forensics & OSINT** — Examining memory dumps, network captures (PCAP), and steganographic images has built a methodical evidence-collection mindset that mirrors real incident-response work.
- **Team collaboration** — Competing on a team taught me how to divide challenges by strength, communicate partial findings clearly, and avoid duplicating effort under time pressure.

The National Cyber League (NCL) competition in particular gave me structured benchmarks — individual and team scoring across multiple categories — that let me see exactly where I excel and where I need to grow.

> **Note:** In accordance with NCL policies, this portfolio does not contain public-facing write-ups or solutions to NCL-specific challenges.

---

## CTF Highlights

### PicoCTF — Web Exploitation Challenge: *Cookies*

**Category:** Web Exploitation  
**Difficulty:** Easy  
**Tools used:** Browser DevTools, Python `requests`

**Summary:**  
The challenge presented a cookie-based authentication mechanism. After logging in as a guest user I noticed the `auth` cookie was a simple base64-encoded JSON object:

```
{"user": "guest", "admin": false}
```

I decoded the value, changed `"admin": false` to `"admin": true`, re-encoded it, and replaced the cookie. The server trusted the client-supplied value without a signature, so it immediately granted admin access and revealed the flag.

**Key takeaway:** Never trust client-supplied data without a cryptographic integrity check (e.g., HMAC signing). This is the exact vulnerability class behind many real-world session-hijacking incidents.

---

### TryHackMe — Room: *Pickle Rick*

**Category:** Linux / Web Exploitation  
**Difficulty:** Easy  
**Tools used:** `nmap`, `gobuster`, Burp Suite, `curl`

**Summary:**  
Starting from an externally exposed web server, I used `gobuster` to discover a hidden `/robots.txt` file that leaked a username. A command-injection vulnerability in the web application's ingredient-lookup feature allowed me to execute arbitrary system commands. By listing the file system I found three flag files, each gated behind escalating privilege levels. The final root flag required leveraging `sudo` permissions that had been misconfigured to allow passwordless execution of any command.

**Key takeaway:** Information disclosure through `robots.txt` and misconfigured `sudo` rules are both classic findings in penetration tests. Defense-in-depth — restricting what users can run with `sudo` and sanitizing all user-supplied input — would have prevented the full chain.

---

### NCL Individual Game

I competed in the NCL Individual Game across multiple seasons, placing in the **Gold bracket**. My strongest categories were:

- **Log Analysis** — identified attacker behavior from web server and authentication logs
- **Scanning & Reconnaissance** — enumerated services and OS fingerprints across target machines
- **Network Traffic Analysis** — reconstructed attack sessions from PCAP files

Per NCL policy, challenge-specific details and solutions are not included here.

---

## NCL Scouting Reports

Scouting Reports are an official NCL artifact that summarizes individual and team performance across all competition categories. They provide recruiters and hiring managers with a verified, third-party snapshot of demonstrated skills.

| Report | Link |
|--------|------|
| Individual Scouting Report | *[Public share link — add yours here]* |
| Team Scouting Report | *[Public share link — add yours here]* |

> **Tip:** To make your scouting report public, log in to the NCL portal, navigate to your report, and select "Share → Public Link."

---

## Connect

- **GitHub:** [github.com/nick-pine](https://github.com/nick-pine)
- **LinkedIn:** *[Add your LinkedIn URL here]*
- **Email:** *[Add your contact email here]*
