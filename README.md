# M365 PowerShell Toolkit

An interactive, browser-based reference tool for Microsoft 365 PowerShell commands. Built for IT admins and consultants who work with M365 tenants daily.

**No install required** — just open `index.html` in your browser, or use the [live version via GitHub Pages](#deploy-with-github-pages).

## ✨ Features

| Feature | Description |
|---|---|
| **170+ Commands** | Covering Users, Groups, Exchange, SharePoint, Teams, Intune, Conditional Access, Security & more |
| **9 Modules** | Microsoft Graph, Exchange Online, Teams, SharePoint, PnP, Intune, Entra ID, MSCommerce, EOP/SCC |
| **Editable Parameters** | Set your domain once — every command updates automatically |
| **Script Builder** | Check commands → generate a complete `.ps1` script with install, connect, commands, disconnect |
| **Workflow Templates** | Pre-built checklists: User Onboarding, Offboarding, Security Audit, Tenant Health Review |
| **Favorites** | Star commands you use often — persisted in your browser |
| **Copy as Full Script** | One-click copy of install + connect + command for any entry |
| **Search & Filter** | Filter by category, module, or free-text search |
| **Fully Offline** | Single HTML file, no dependencies, works without internet |

## 🚀 Quick Start

### Option 1: Download and open

1. Download `index.html`
2. Double-click to open in any browser
3. Done

### Option 2: Clone the repo

```bash
git clone https://github.com/Great-IT-Nordic/m365-ps-toolkit.git
cd m365-ps-toolkit
# Open index.html in your browser
start index.html        # Windows
open index.html         # macOS
xdg-open index.html     # Linux
```

## 🌐 Deploy with GitHub Pages

You can host this as a live site for your team:

1. Go to your repo **Settings** → **Pages**
2. Under "Source", select **Deploy from a branch**
3. Choose `main` branch and `/ (root)` folder
4. Click **Save**
5. Your toolkit will be live at `https://great-it-nordic.github.io/m365-ps-toolkit/`

## 📁 Project Structure

```
m365-ps-toolkit/
├── index.html          # The complete toolkit (self-contained)
├── README.md           # This file
├── CONTRIBUTING.md     # How to add commands
├── LICENSE             # MIT License
└── docs/
    └── COMMANDS.md     # Full command reference list
```

## 🤝 Contributing

We welcome contributions! The easiest way to help is to **add new commands**.

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed instructions, but the short version:

1. Fork the repo
2. Open `index.html` in a text editor
3. Find the `COMMANDS` array (search for `const COMMANDS`)
4. Add your command following the existing format:
   ```javascript
   { cat: "Category", name: "Command name", cmd: 'Your-Command -Here', module: "ModuleName", desc: "What it does" },
   ```
5. Submit a Pull Request

### Parameter placeholders

Use these in your commands and they'll be replaced by user input:

| Placeholder | Replaced with | Example |
|---|---|---|
| `{{domain}}` | User's domain | `contoso.com` |
| `{{admin}}` | Admin UPN | `admin@contoso.com` |
| `{{spo}}` | SPO admin URL | `contoso-admin.sharepoint.com` |

## 📦 Modules Covered

| Module | Short | Used for |
|---|---|---|
| `Microsoft.Graph` | Graph | Users, Groups, Licensing, Entra ID, Reports |
| `ExchangeOnlineManagement` | EXO | Mailboxes, Mail Flow, Transport Rules |
| `MicrosoftTeams` | Teams | Teams, Channels, Policies |
| `Microsoft.Online.SharePoint.PowerShell` | SPO | Site Collections, OneDrive, Sharing |
| `PnP.PowerShell` | PnP | Lists, Libraries, Site Content |
| `Microsoft.Graph.Identity.DirectoryManagement` | Entra | Directory Roles, Conditional Access |
| `Microsoft.Graph.DeviceManagement` | Intune | Devices, Compliance, Autopilot |
| `MSCommerce` | Commerce | Self-Service Purchase Policies |
| `ExchangeOnlineProtection` | EOP/SCC | DLP, Retention, Sensitivity Labels |

## 📋 Command Categories

- **User Management** — Create, disable, delete, export, MFA status, auth methods
- **Group Management** — Security groups, M365 groups, dynamic groups, distribution lists
- **Licensing** — SKU overview, assign/remove, find unlicensed users
- **Exchange Online** — Mailboxes, permissions, calendars, forwarding, timezone, holds
- **Mail Flow & Transport** — Transport rules, message trace, quarantine, DKIM, connectors
- **SharePoint Online** — Sites, storage, sharing, OneDrive, PnP operations
- **Teams** — Teams, channels, members, policies, archiving
- **Security & Compliance** — Admin roles, MFA, risky users, sign-in logs, app registrations, DLP
- **Conditional Access** — Policies, named locations, export/backup
- **Device Management** — Intune devices, compliance, Autopilot, remote actions
- **Reports & Auditing** — Usage reports, audit logs, activity reports
- **Tenant Configuration** — Org details, domains, auth methods, password policies

## 🔧 Workflow Templates

### 🚀 User Onboarding
Step-by-step: create account → assign license → add to groups → configure mailbox → set manager → add to Teams

### 🔒 User Offboarding
Step-by-step: disable sign-in → revoke sessions → set OOO → convert to shared → delegate access → remove licenses → clean up forwarding

### 🛡️ Security Audit
Check: Global Admins → MFA status → CA policies → risky sign-ins → app credentials → external sharing → forwarding rules → audit logs

### 📊 Tenant Health Review
Review: license usage → unlicensed users → active users → mailbox sizes → SharePoint storage → stale devices → tenant config

## 📄 License

MIT — use it, fork it, share it.

## 🙏 Credits

Built by [Great IT Nordic](https://github.com/Great-IT-Nordic) for the Microsoft 365 admin community.
