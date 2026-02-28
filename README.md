# M365 PowerShell Toolkit

> 224 ready-to-use PowerShell commands for Microsoft 365 administration — in a single, self-contained HTML file.

**[🚀 Open the Toolkit](https://great-it-nordic.github.io/m365-ps-toolkit/)** · Built by [Great IT Nordic](https://greatit.se/en/)

---

## What is this?

A zero-install, browser-based reference tool for M365 admins. Every command is copy-paste ready, tagged with risk level and required permissions, and organized into 13 categories with 7 built-in workflows and a custom workflow builder.

No backend. No dependencies. One HTML file — works offline.

## Quick Start

1. **Open** the toolkit in your browser (or download `index.html` and open locally)
2. **Set your domain** — click ⚙️ Parameters and enter your tenant domain. All commands auto-update.
3. **Browse or search** — filter by category, module, workflow, or use `Ctrl+K` to search
4. **Copy and run** — expand any command, hit Copy, paste into PowerShell

```powershell
# Your first command in 30 seconds
Install-Module Microsoft.Graph -Scope CurrentUser
Connect-MgGraph -Scopes "User.Read.All"
Get-MgUser -All | Select DisplayName, UserPrincipalName, AccountEnabled
```

## Coverage

| Category | Commands | Examples |
|---|---|---|
| User Management | 24 | Create, disable, reset password, bulk export, group memberships |
| Group Management | 15 | Security groups, M365 groups, dynamic membership, expiration |
| Licensing | 8 | Assign, remove, license paths, SKU overview |
| Exchange Online | 33 | Mailbox config, shared mailboxes, permissions, delegates, archive |
| Mail Flow & Transport | 10 | Transport rules, DKIM, anti-spam, quarantine, blocked senders |
| SharePoint Online | 17 | Sites, storage, external sharing, hub sites, recycle bin |
| Teams | 15 | Team management, channels, policies, guest config, apps |
| Security & Compliance | 30 | Defender, DLP, retention, Secure Score, risky users, eDiscovery |
| Conditional Access | 14 | Policies, named locations, auth strengths, create/delete/export |
| Entra ID Governance | 11 | Access packages, access reviews, lifecycle workflows, PIM, ToU |
| Device Management | 25 | Intune devices, compliance, apps, Autopilot, remote actions |
| Reports & Auditing | 13 | Usage reports, sign-in logs, audit logs, MFA registration |
| Tenant Configuration | 9 | Org details, domains, auth methods, password policy, sync status |

**Total: 224 commands** — 167 read · 45 modify · 12 destructive

## Features

### Core

- **Search** — full-text across names, descriptions, PowerShell syntax, modules, and permissions. Supports operators: `risk:destructive`, `module:exchange`, `perm:User.Read`, `cat:teams`
- **Risk indicators** — every command tagged 🟢 Read, 🟡 Modify, or 🔴 Destructive
- **Permissions** — Graph API scopes displayed per command
- **Tenant profiles** — save domain, admin UPN, and SPO URL per client for instant switching
- **Deep links** — URL updates as you navigate. Share a link to any category, workflow, or search result

### Productivity

- **Script Builder** — check multiple commands, add error handling / transcript logging / `#Requires`, download as `.ps1`
- **Connection Builder** — select your tasks, get the exact `Connect-*` commands with the right scopes
- **Permissions Calculator** — auto-generates the minimal `Connect-MgGraph -Scopes` from your favorites, builder selection, or current view
- **CSV templates** — downloadable templates for bulk operations
- **Favorites & notes** — star commands and add personal notes, persisted in localStorage

### Workflows

7 built-in step-by-step workflows with progress tracking:

1. 🚀 **User Onboarding** — account creation through CA policy verification (8 steps)
2. 🔒 **User Offboarding** — disable, revoke, forward checks, shared mailbox conversion (9 steps)
3. 🛡️ **Security Audit** — admins, MFA, CA, risky sign-ins, app credentials, audit logs (10 steps)
4. 📊 **Tenant Health Review** — licenses, mailbox sizes, storage, stale devices (9 steps)
5. 💰 **License Cleanup** — find and reclaim unused licenses (8 steps)
6. 📧 **Mail Hygiene Review** — forwarding, transport rules, DKIM, anti-phish, quarantine (10 steps)
7. 👥 **Guest Access Audit** — guest users, external sharing, consent grants (8 steps)

**Custom Workflows** — create your own from any commands. Click **+** next to "Workflows" in the sidebar. Progress persists across sessions and is included in settings export/import.

### Quality of Life

- **Syntax highlighting** — color-coded PowerShell (cmdlets, parameters, strings, variables, comments, operators)
- **Graph sub-module mapping** — shows the precise `Import-Module` for each command (e.g. `Microsoft.Graph.Users`)
- **Two-button copy** — "Install + Import + Connect" for first-time setup, "Import + Connect" for daily use
- **Destructive command warnings** — red toast when copying delete/remove commands
- **Parameter hints** — placeholders show which command to run first to find the required ID
- **Legacy command map** — see the deprecated AzureAD/MSOL equivalent for each command
- **Settings export/import** — backup and restore all favorites, notes, profiles, workflows, and progress
- **Prerequisite checker** — generates a script to verify and install all required modules
- **Dark/light theme** with 🌙 toggle
- **Keyboard shortcuts** — `Ctrl+K` search, `↑↓` navigation, `Enter` expand, `Esc` close

## Modules

| Module | Used for |
|---|---|
| Microsoft.Graph | Users, Groups, Identity, Reports, Security, Devices |
| ExchangeOnlineManagement | Mailboxes, transport, protection |
| MicrosoftTeams | Teams, channels, policies |
| Microsoft.Online.SharePoint.PowerShell | SPO tenant admin |
| PnP.PowerShell | Site-level SPO operations |
| MSCommerce | Self-service purchase policies |

All commands use **Graph SDK v2** syntax. Legacy AzureAD/MSOL cmdlets are shown as references only.

## Prerequisites

- **PowerShell 7+** — [Download](https://github.com/PowerShell/PowerShell/releases)
- **Admin roles** — most commands need Global Admin, Exchange Admin, Teams Admin, or Intune Admin. Check the permissions tag per command.
- **Modules** — use the Prerequisite Checker in Module Setup, or install manually:

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser -Force
Install-Module ExchangeOnlineManagement -Force
Install-Module MicrosoftTeams -Force
Install-Module Microsoft.Online.SharePoint.PowerShell -Force
Install-Module PnP.PowerShell -Force
```

## Self-Hosting

Download `index.html` and open it. Works from:

- Local file (`file:///`)
- GitHub Pages (like the live version)
- Any static host (Azure Static Web Apps, Netlify, your intranet)
- SharePoint document library

No build step, no npm, no API calls. Client-side only with localStorage.

## Contributing

Found a missing command or syntax issue?

**Quick:** [Open an issue](https://github.com/Great-IT-Nordic/m365-ps-toolkit/issues/new?title=Command+suggestion:+&labels=enhancement) with the command name, PowerShell syntax, and category.

**Full:** Fork → edit the `COMMANDS` array in `index.html` → PR.

Command structure:

```javascript
{
  cat: "Category Name",
  name: "Human-readable name",
  cmd: "Actual-PowerShell-Command -With \"parameters\"",
  module: "Module.Name",
  desc: "What this command does",
  risk: "read",        // read | modify | destructive
  perms: "Scope.Name", // Graph API permissions (optional)
  related: ["Other command name"],  // optional
  csv: "Col1,Col2,Col3"            // optional CSV template columns
}
```

## Changelog

### v2.0

- **48 new commands** (176 → 224) across Defender, Intune, Entra Governance, Exchange, SharePoint, Teams
- **Entra ID Governance** — new category with 11 commands (access packages, reviews, lifecycle workflows, PIM)
- **Permissions Calculator** — auto-generates minimal `Connect-MgGraph -Scopes` from selected commands
- **Custom Workflows** — create, save, and track your own step-by-step workflows
- Security & Compliance expanded with Secure Score, threat alerts, eDiscovery, risky user actions
- Intune expanded with managed apps, remote lock/restart, encryption status, Settings Catalog
- Exchange expanded with shared/room mailboxes, permissions, delegates, Send As
- SharePoint expanded with hub sites, site permissions, recycle bin
- Teams expanded with meeting/messaging/app setup policies, guest config

### v1.5

- PowerShell syntax highlighting (8 token types, light/dark)
- Graph sub-module mapping (60+ cmdlets → precise imports)
- Two-button script copy (Install+Import+Connect vs Import+Connect)
- Destructive command copy warnings
- Parameter value hints
- Search operators (`risk:`, `module:`, `perm:`, `cat:`)
- Settings export/import (JSON backup/restore)
- Prerequisite checker script

### v1.0

- 176 commands across 12 categories
- 7 built-in workflows with progress tracking
- Script Builder with .ps1 download
- Connection Builder
- Tenant profiles, favorites, notes, command history
- Dark/light theme, deep links, keyboard navigation

## License

MIT

---

Built with ❤️ by [Great IT Nordic](https://greatit.se/en/) — Microsoft 365 specialists based in Sweden.
