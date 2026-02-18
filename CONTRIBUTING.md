# Contributing to M365 PowerShell Toolkit

Thanks for wanting to contribute! This guide will help you add commands, fix bugs, or improve the tool.

## Adding New Commands

This is the most common contribution. Here's exactly how to do it.

### 1. Fork & Clone

```bash
git clone https://github.com/YOUR-USERNAME/m365-ps-toolkit.git
cd m365-ps-toolkit
```

### 2. Edit `index.html`

Open the file in any text editor (VS Code recommended). Search for `const COMMANDS = [` to find the commands array.

### 3. Add your command

Follow this format:

```javascript
{ cat: "Category", name: "Short name", cmd: 'The-PowerShell-Command -With "parameters"', module: "ModuleName", desc: "One-line description", risk: "read", perms: "Scope.Name" },
```

**Example:**

```javascript
{ cat: "Exchange Online", name: "Get mailbox audit settings", cmd: 'Get-Mailbox -Identity "user@{{domain}}" | Select AuditEnabled,AuditLogAgeLimit', module: "ExchangeOnlineManagement", desc: "Check if mailbox auditing is enabled", risk: "read" },
```

### Rules

- **Place commands under the correct category comment** (e.g., `// ── EXCHANGE ONLINE ──`)
- **Use `{{domain}}`, `{{admin}}`, `{{spo}}`** as parameter placeholders (see below)
- **Test the command** in your own tenant before submitting
- **Keep the description short** — one line, no period at the end
- **Use the exact module name** from the `MODULES` object at the top of the file
- **Escape quotes properly** — use single quotes for outer, double for inner (or vice versa)

### Parameter Placeholders

| Placeholder | Description | Default |
|---|---|---|
| `{{domain}}` | Tenant domain | `domain.com` |
| `{{admin}}` | Admin user UPN | `admin@domain.com` |
| `{{spo}}` | SharePoint admin URL | `domain-admin.sharepoint.com` |

### Valid Categories

Use one of these exact strings:

- `User Management`
- `Group Management`
- `Licensing`
- `Exchange Online`
- `Mail Flow & Transport`
- `SharePoint Online`
- `Teams`
- `Security & Compliance`
- `Conditional Access`
- `Device Management`
- `Reports & Auditing`
- `Tenant Configuration`

Want to add a new category? Open an issue first so we can discuss.

### Valid Modules

- `Microsoft.Graph`
- `ExchangeOnlineManagement`
- `MicrosoftTeams`
- `Microsoft.Online.SharePoint.PowerShell`
- `PnP.PowerShell`
- `AzureAD (Graph)`
- `Microsoft.Graph.Intune`
- `MSCommerce`
- `ExchangeOnlineProtection`

### Risk Levels (required)

Every command must have a `risk` field:

| Value | Badge | When to use |
|---|---|---|
| `"read"` | 🟢 Read | Only retrieves data, no changes |
| `"modify"` | 🟡 Modify | Creates or changes settings |
| `"destructive"` | 🔴 Destructive | Deletes, wipes, or removes permanently |

### Permissions (optional)

For Microsoft Graph commands, add a `perms` field with the required Graph API scope(s):

```javascript
perms: "User.Read.All"              // single scope
perms: "AuditLog.Read.All, User.Read.All"  // multiple scopes
```

Omit `perms` for non-Graph modules (EXO, Teams, SPO) — they use role-based access instead of Graph scopes.

### 4. Test locally

Open `index.html` in your browser and verify:
- Your command shows up in the correct category
- The module badge displays correctly
- Search finds your command
- Copy button works
- Parameters get replaced when you fill in the Parameters bar

### 5. Submit a Pull Request

```bash
git checkout -b add-mailbox-audit-command
git add index.html
git commit -m "Add: Get mailbox audit settings command"
git push origin add-mailbox-audit-command
```

Then open a PR on GitHub.

## Adding New Workflows

Workflows are in the `WORKFLOWS` object. Format:

```javascript
"wf-your-workflow": {
  name: "🎯 Workflow Name",
  desc: "What this workflow does.",
  steps: [
    "Step 1 description",
    "Step 2 description"
  ],
  commands: ["Command Name 1", "Command Name 2"]  // Must match exact command names
}
```

## Adding New Modules

Modules are in the `MODULES` object:

```javascript
"Module.Name": {
  install: "Install-Module -Name Module.Name -Force",
  connect: "Connect-Something -Parameter value",
  disconnect: "Disconnect-Something",
  color: "#HexColor",
  short: "SHORT"
}
```

## Bug Reports

Open an issue with:
- What you expected
- What happened
- Browser and OS
- Screenshot if possible

## Code Style

- This is intentionally a single HTML file for simplicity — keep it that way
- Use `var(--css-variable)` for colors
- Keep JavaScript vanilla (no frameworks)
- Test on Chrome and Edge at minimum

## Commit Messages

Use prefixes:
- `Add:` for new commands or features
- `Fix:` for bug fixes
- `Update:` for changes to existing commands
- `Docs:` for README/docs changes
