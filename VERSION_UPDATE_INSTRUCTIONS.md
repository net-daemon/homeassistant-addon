# Instructions for Adding a New NetDaemon Version

This document provides step-by-step instructions for adding a new NetDaemon version to the Home Assistant addon repository.

## Prerequisites

- Identify the new .NET version number (e.g., .NET 11)
- Identify the new NetDaemon version number (e.g., V7)
- Determine the new addon version number following the pattern (e.g., 27.0.0)

## Steps to Add a New Version

### 1. Create New Addon Directory

Create a new directory for the version following the naming pattern `netdaemon_X` where X is the version number.

Example: `netdaemon_7/`

### 2. Copy Required Files

Copy the following files from the most recent stable version (not alpha):

```bash
# From netdaemon_6/ to netdaemon_7/
cp -r netdaemon_6/* netdaemon_7/
```

### 3. Update config.json

Update the following fields in `netdaemon_7/config.json`:

- `name`: Update to "NetDaemon VX (.NET YY)" (e.g., "NetDaemon V7 (.NET 11)")
- `version`: Increment following the pattern (e.g., "27.0.0")
- `slug`: Update to "netdaemonX" (e.g., "netdaemon7")
- `description`: Update to match the new version and .NET version
- `image`: Update to "ghcr.io/net-daemon/netdaemon_addonX" (e.g., "ghcr.io/net-daemon/netdaemon_addon7")
- `options.app_config_folder`: Update to "/config/netdaemonX" (e.g., "/config/netdaemon7")

### 4. Update README.md

Update `netdaemon_7/README.md`:

- Update the title to reflect the new version
- Update all references to the version number
- Update the .NET version mentioned in the text
- Update deprecation warnings to reference the new version as current

Example:
```markdown
# NetDaemon V7 (.NET 11)

NetDaemon provides capability to write home automations in C# for Home Assistant.
This is the version 7 of the NetDaemon runtime using .NET 11.

**If you are still running the 3.x, 4.x, 5.x or 6.x version of NetDaemon, Please select correct version of the add-on. We are recommending users to upgrade to V7 asap.**
```

### 5. Update translations/en.json

Update `netdaemon_7/translations/en.json`:

- Update `app_config_folder.description` to reference the new default path

Example:
```json
"app_config_folder": {
    "name": "App configuration folder",
    "description": "Path for application configuration (default=/config/netdaemon7)"
}
```

### 6. Update Previous Version READMEs

Update README files from previous versions to point to the new version as current:

**Previous stable version (e.g., netdaemon_6/README.md):**
```markdown
** We are recommending users to upgrade to V7 asap since no new features or fixes will be done in this version**
```

**Older deprecated versions (e.g., netdaemon_5/README.md, netdaemon_4/README.md, netdaemon3_1/README.md):**
Update any references from "upgrade to VX" to "upgrade to V7"

### 7. Verify Files

Verify all files are present:
- `config.json`
- `README.md`
- `CHANGELOG.md`
- `translations/en.json`
- `icon.png`
- `logo.png`

### 8. Validate JSON

Ensure JSON files are valid:
```bash
python3 -c "import json; json.load(open('netdaemon_7/config.json'))"
python3 -c "import json; json.load(open('netdaemon_7/translations/en.json'))"
```

## Version Pattern Reference

| NetDaemon Version | .NET Version | Addon Version Pattern | Slug |
|------------------|--------------|----------------------|------|
| V3.0 | .NET 6 | 22.x.x | netdaemon3 |
| V3.1 | .NET 7 | 23.x.x | netdaemon3_1 |
| V4 | .NET 8 | 24.x.x | netdaemon4 |
| V5 | .NET 9 | 25.x.x | netdaemon5 |
| V6 | .NET 10 | 26.x.x | netdaemon6 |
| V7 | .NET 11 | 27.x.x | netdaemon7 |

## Notes

- Do NOT modify `.github/stale.yml` for version updates
- The addon version number major version typically matches: 20 + (.NET version - 4)
  - .NET 6 → 22.x.x
  - .NET 7 → 23.x.x
  - .NET 8 → 24.x.x
  - etc.
- Alpha/pre-release versions use the `netdaemon_alpha` directory and are handled separately
- Ensure all version references are updated consistently across all files
