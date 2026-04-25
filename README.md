# linux-forge 🔧

An Ansible project to automate the base configuration and hardening of Linux servers (Ubuntu 24.04).

## What it does

- **Common** — system update, base packages installation, timezone configuration, admin user creation
- **SSH** — OpenSSH hardening (disable root login, disable password authentication, limit auth attempts)
- **Firewall** — UFW configuration with default deny incoming policy
- **Fail2ban** — brute-force protection with automatic IP banning

## Requirements

- Ansible 2.14+
- Target hosts: Ubuntu 24.04 LTS
- SSH access to target hosts

## Project structure

\`\`\`
linux-forge/
├── inventory/
│   ├── hosts.ini
│   └── group_vars/
│       └── all.yml
├── roles/
│   ├── common/
│   ├── ssh/
│   ├── firewall/
│   └── fail2ban/
├── playbooks/
│   └── site.yml
├── ansible.cfg
└── requirements.yml
\`\`\`

## Usage

1. Clone the repository:
\`\`\`bash
git clone https://github.com/dennisgallina/linux-forge.git
cd linux-forge
\`\`\`

2. Copy the inventory example and edit with your hosts:
\`\`\`bash
cp inventory/hosts.ini.example inventory/hosts.ini
\`\`\`

3. Set up Ansible Vault for sensitive variables:
\`\`\`bash
ansible-vault create group_vars/all/vault.yml
\`\`\`

4. Run the playbook:
\`\`\`bash
ansible-playbook playbooks/site.yml
\`\`\`

## Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `system_timezone` | `Europe/Rome` | System timezone |
| `admin_user` | `dennis` | Admin username to create |
| `ssh_port` | `22` | SSH port |
| `fail2ban_maxretry` | `5` | Max failed attempts before ban |
| `fail2ban_bantime` | `3600` | Ban duration in seconds |
| `fail2ban_findtime` | `600` | Time window for failed attempts |

## Tested on

- Ubuntu 24.04 LTS

## License

MIT
