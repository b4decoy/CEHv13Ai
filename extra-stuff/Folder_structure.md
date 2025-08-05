```
ceh13ai/
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt      # (if using Python or tools)
│
├── modules/              # CEH modules by domain/topic
│   ├── 01_reconnaissance/
│   │   ├── notes.md
│   │   ├── tools.md
│   │   └── examples/
│   │       └── whois_enum.sh
│   ├── 02_scanning/
│   ├── 03_gaining_access/
│   ├── 04_maintaining_access/
│   └── 05_covering_tracks/
│
├── notes/                # General or combined notes
│   ├── cheatsheets/
│   │   └── nmap_cheatsheet.md
│   ├── attack_matrix.md
│   └── oscp_vs_ceh.md
│
├── scripts/              # Custom tools or automation
│   ├── passive_enum.py
│   ├── ssh_brute.py
│   └── portscanner.py
│
├── tools/                # Tool references or configs
│   ├── metasploit/
│   │   └── usage.md
│   ├── nmap/
│   │   └── custom_scripts/
│   └── burpsuite/
│       └── config.json
│
├── resources/            # External files, PDFs, links
│   ├── ebooks/
│   ├── pci-dss/
│   └── CVE-database/
│
├── labs/                 # Practice labs
│   ├── vuln-vms/
│   └── walkthroughs/
│       └── metasploitable2.md
│
└── ai/                   # Future AI automation helpers
    ├── README.md
    ├── ceh_bot.py
    └── gpt_prompts/
        └── recon_gpt_prompt.txt

```



#Script 


```
#!/bin/bash

ROOT="ceh13ai"

echo "📁 Setting up project structure in ./$ROOT..."

# Create folder tree
mkdir -p $ROOT/{modules/{01_reconnaissance/examples,02_scanning,03_gaining_access,04_maintaining_access,05_covering_tracks},\
notes/cheatsheets,scripts,tools/{metasploit,nmap/custom_scripts,burpsuite},resources/{ebooks,pci-dss,CVE-database},\
labs/{vuln-vms,walkthroughs},ai/gpt_prompts}

# Create placeholder files (only if not already present)
touch $ROOT/{README.md,LICENSE,.gitignore,requirements.txt}

# Modules
touch $ROOT/modules/01_reconnaissance/{notes.md,tools.md}
touch $ROOT/modules/01_reconnaissance/examples/whois_enum.sh

# Notes
touch $ROOT/notes/cheatsheets/nmap_cheatsheet.md
touch $ROOT/notes/attack_matrix.md
touch $ROOT/notes/oscp_vs_ceh.md

# Scripts
touch $ROOT/scripts/{passive_enum.py,ssh_brute.py,portscanner.py}

# Tools
touch $ROOT/tools/metasploit/usage.md
touch $ROOT/tools/burpsuite/config.json

# Labs
touch $ROOT/labs/walkthroughs/metasploitable2.md

# AI helpers
touch $ROOT/ai/{README.md,ceh_bot.py}
touch $ROOT/ai/gpt_prompts/recon_gpt_prompt.txt

echo "✅ Structure updated inside existing folder: ./$ROOT"

```


