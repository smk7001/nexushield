<div align="center">

<img src="https://github.com/user-attachments/assets/177ab44b-2af0-4d18-b73b-76d4307a6705" alt="Nexu Shield logo" width="140">



# NexuShield AntiVirus

**A Windows desktop security suite built in Python, bringing malware scanning, firewall control, USB protection and system cleanup into one interface.**

![Python](https://img.shields.io/badge/Python-3.13-3776AB?logo=python&logoColor=white)
![Tkinter](https://img.shields.io/badge/GUI-Tkinter-2E3B4E)
![MySQL](https://img.shields.io/badge/MySQL-Signature%20DB-4479A1?logo=mysql&logoColor=white)
![Windows](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)
![Signatures](https://img.shields.io/badge/Signatures-1.1M%2B-c0392b)

</div>


---

## Features

**False-positive protection:** Matches that are genuine, Microsoft-signed Windows files are filtered out automatically. 

**Virus Scan:** Scans the system drive and checks files against **1.1M+ known malware signatures** from MalwareBazaar, then lets you review and remove matches. 


<img width="377" height="320" alt="Capture9" src="https://github.com/user-attachments/assets/9f25028f-4565-4413-89b5-5b46afa1c578" />

<img width="382" height="311" alt="Capture5" src="https://github.com/user-attachments/assets/9335ae73-b3a1-4f5a-9d35-e1e1ab87c025" />

<img width="384" height="345" alt="Capture" src="https://github.com/user-attachments/assets/6a9c615b-651c-442d-8b94-2cf855e9bb9a" />


**Firewall:** View, create and delete inbound and outbound firewall rules. 

<img width="382" height="275" alt="Capture3" src="https://github.com/user-attachments/assets/a39a973a-f514-4653-bd14-671ec03e6cb1" />

<img width="378" height="277" alt="Capture6" src="https://github.com/user-attachments/assets/b069e051-8b43-41b7-8f6d-2b7c14438e48" />

<img width="380" height="315" alt="Capture8" src="https://github.com/user-attachments/assets/bcac277c-f9d8-457f-8632-8c10dface941" />



**USB Protection:** Blocks USB storage by default, with per-device enable/disable. 

<img width="383" height="278" alt="Capture4" src="https://github.com/user-attachments/assets/455cfea6-78f2-4274-a6f4-64dc691fa446" />


**Junk Cleaner:** Clears temporary files, caches and other system clutter. 

<img width="380" height="276" alt="Capture2" src="https://github.com/user-attachments/assets/b4b5b7e2-81e8-4390-b393-a9c3c0b70b41" />




## How detection works

```mermaid
flowchart LR
    A[Scan drive] --> B[Hash files]
    B --> C[(Signature DB)]
    C --> D[Filter trusted<br/>Microsoft files]
    D --> E[Review & remove]
```

1. **Scan:** files are fingerprinted with MD5, SHA-1 and SHA-256 using multiple threads.
2. **Match:** fingerprints are checked against a MySQL database of known malware.
3. **Verify:** matches with a valid Microsoft signature are treated as false positives.
4. **Act:** the remaining matches are listed for review before anything is deleted.

## Skills demonstrated

**Security**
- Signature-based malware detection and cryptographic hashing
- Integrating a real-world threat-intelligence feed (MalwareBazaar)
- Handling false positives through code-signature verification
- Host hardening: firewall rules and removable-media control

**Software engineering**
- Modular design, with one module per feature
- Multithreading, with a responsive UI during long-running scans
- Resilient error handling: unreadable files are logged and skipped, not fatal
- Batched database queries for large signature sets

**Systems and tooling**
- Integrating Python with Windows system tools and APIs
- Automated setup: dependency installer and database loader scripts
- Debugging real platform issues, such as long paths and certificate validation

## Project structure

```text
├── avav.py           # Main window and navigation
├── hashav.py         # File scanner and hashing
├── qav.py            # Signature lookup, trust check, removal UI
├── fwav.py           # Firewall management
├── usbav.py          # USB protection
├── diskav.py         # Junk cleaner
├── setup_db.py       # Creates the database and loads signatures
├── check_file.py     # Diagnostic: explains why a file is or isn't detected
├── install.ps1       # One-step dependency installer
└── requirements.txt
```

## Upcoming Updates

- [ ] Quarantine (move and restore) instead of permanent deletion
- [ ] Real-time file monitoring
- [ ] Heuristic / YARA-based detection
- [ ] Package as a standalone `.exe`

## Acknowledgements

Malware signatures provided by [MalwareBazaar](https://bazaar.abuse.ch/) (abuse.ch).

---

<div align="center">

Built by **Sebastian Kolesnik** · © 2025

</div>
