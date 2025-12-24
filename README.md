# TheraPrac Workspace

This is the workspace root for the TheraPrac platform. It contains workspace-level configuration and documentation that applies across all projects.

## Structure

```
theraprac-workspace/
├── .code-workspace          # VS Code/Cursor workspace file
├── .cursor/                 # Workspace-level Cursor configuration
│   ├── rules.md            # AI agent rules for all projects
│   ├── WORKSPACE.md        # Workspace documentation spine
│   ├── DOCUMENTATION_AUDIT_REPORT.md
│   └── agents/
│       └── bugfix.md       # BugFix Agent contract
└── README.md               # This file
```

## Projects

This workspace includes:
- `theraprac-api` - Go backend API
- `theraprac-web` - Next.js frontend
- `theraprac-infra` - Terraform/Ansible infrastructure
- `ziti-source` - Go networking library (external)
- `otel-trace` - OpenTelemetry tracing utilities
- `scripts` - Shared helper scripts

## Documentation

See `.cursor/WORKSPACE.md` for the workspace documentation spine and how documentation authority works across projects.

## Opening the Workspace

Open `theraprac.code-workspace` in Cursor or VS Code to load all projects.

