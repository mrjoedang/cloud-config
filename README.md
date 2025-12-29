# cloud-config

A cloud-init configuration for provisioning Ubuntu servers on Hetzner Cloud.

## Usage

```bash
hcloud server create --type cx23 --image ubuntu-24.04 --location nbg1 \
  --user-data-from-file <(curl -fsSL https://raw.githubusercontent.com/mrjoedang/cloud-config/main/cloud-config.yml) \
  --name my-server
```

Or if you have the file locally:

```bash
hcloud server create --type cx23 --image ubuntu-24.04 --location nbg1 \
  --user-data-from-file cloud-config.yml \
  --name my-server
```

After provisioning, connect via:

```bash
ssh holu@<server-ip> -p 2222
```

## What's Included

**Security**
- SSH hardened (key-only auth, non-standard port 2222, root login disabled)
- fail2ban configured for SSH
- UFW firewall enabled

**Tools**
- Node.js (via fnm)
- Neovim with LazyVim
- Yazi file manager
- Tailscale

**Utilities**
- opencode-ai
- ripgrep, fd, fzf
- jq, curl, git
- ffmpeg, imagemagick
- btop, atuin
