# Project-1

Simple static site deployed to Raspberry Pi.

## Structure

```
.
├── index.html    # Main page
├── style.css     # Styling (dark theme)
└── README.md     # This file
```

## Deployment

**Pi Location:** `ryan@192.168.4.37:~/web/project-1/`

**Access:** http://mypi.local/

### Architecture

**Pi Setup:**
- Hostname: `mypi`
- nginx reverse proxy (port 80) → Python server (port 5000)
- avahi-daemon running (mDNS broadcast)
- nginx config: `/etc/nginx/sites-available/project1`

**Local Machine (WSL):**
- `/etc/hosts` entry: `192.168.4.37  mypi.local mypi`
- `/etc/wsl.conf` set to `generateHosts = false`

**Network-wide:**
- Currently WSL-only via /etc/hosts
- Mac/Linux devices may auto-resolve via mDNS (avahi)
- Windows needs Bonjour for mDNS or manual /etc/hosts

### Commands

**Start Backend:**
```bash
ssh ryan@192.168.4.37
cd web/project-1
python3 -m http.server 5000
```

**Add to /etc/hosts (new devices):**
```bash
echo "192.168.4.37  mypi.local mypi" | sudo tee -a /etc/hosts
```

**Add New Projects:**
Edit `/etc/nginx/sites-available/project1` on Pi, add location blocks

## Git

Repo initialized with initial commit. Branch: `master`

## Notes

- Python server: Built-in, zero deps, static only
- PHP server: Can run PHP scripts
- Node http-server: Fastest, needs npm install
