# Home NAS Server — Ubuntu Server, Samba & Remote Access

Self-built home file server for personal use — network-attached storage accessible
from multiple devices, both locally and remotely.

## What was built

**Base setup**
- Ubuntu Server installed and configured as a VM in VirtualBox
- Firewall (UFW) enabled with SSH access allowed, remote administration confirmed working

**File sharing (Samba)**
- Samba installed and configured with per-device user accounts (not a single shared login)
- Separate shares created for different devices — a laptop file share and a phone backup
  share — each with individually scoped permissions
- Verified working across mixed platforms: mounted and tested on both a Linux device
  (CIFS mount) and a Windows device (File Explorer)
- Configured auto-mount on boot for the Linux client via `/etc/fstab`, so the share
  connects automatically without manual setup each time

**Remote access (Tailscale)**
- Set up Tailscale to allow secure remote access to the server from outside the home
  network (e.g. from campus), without exposing the server directly to the internet
- Connected all devices (server + both laptops) to the same Tailscale network

**Administration**
- Configured an admin user with full sudo access and unrestricted Samba access across
  all shares, separate from the individual device accounts

## What this demonstrates

- Building infrastructure for actual daily use, not just a course requirement — this
  server is genuinely in use
- Troubleshooting real failures under pressure — shares broke mid-project during a
  Tailscale setup, and the fix required isolating whether the issue was networking or
  Samba-specific rather than guessing
- Designing for multiple users/devices with individually scoped access, rather than a
  single shared login
- Balancing convenience (auto-mount, remote access) against security (per-device
  credentials, controlled firewall rules)

## Screenshots
<img width="910" height="274" alt="samba nmb daemon" src="https://github.com/user-attachments/assets/e16983c2-e3c2-4b95-8736-862db2206154" /> sudo systemctl status nmbd
<img width="1089" height="337" alt="smb status" src="https://github.com/user-attachments/assets/b51356d8-21a8-413d-811c-a732ef417553" /> sudo smbstatus
<img width="979" height="801" alt="testparm" src="https://github.com/user-attachments/assets/32b562bd-510a-4d8b-8112-d36a784733f8" /> Testparm
<img width="813" height="133" alt="local host" src="https://github.com/user-attachments/assets/a7311af6-42f0-4c53-a50c-8e5b13fa5226" /> Localhost

## Notes / what I'd do differently

Optional — Would document the Samba troubleshooting process itself next time,
since debugging why shares broke was actually the most useful part of the project
or Considering upgrading hardware to eventually self-host an AI assistant on the
same server.
