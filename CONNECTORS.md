# Connectors

## How tool references work

Plugin files use `~~category` as a placeholder for configurable paths and tools.
When you install this plugin, run the **cowork-plugin-customizer** skill to replace
these placeholders with values specific to your setup.

## Connectors for this plugin

| Placeholder | What it represents | How to configure |
|-------------|-------------------|-----------------|
| `~~skill-vault` | Path to your AI Skill Builder vault directory | Update `config/vault-path.txt` with your full vault path |

## Configuring your vault path

After installing the plugin, update the vault path to point to your skill storage location.

The default value in `config/vault-path.txt` is `~/ai-skill-builder-vault`.

**To change it**, edit `config/vault-path.txt` and replace the contents with your preferred path:

**macOS / Linux:**
```
/Users/yourname/Documents/ai-skill-builder
```

**Windows:**
```
C:\Users\YourName\Workspace\ai-brain-vault\AI Skill Builder
```

The plugin reads this file every time a command runs, so updates take effect immediately.

## Notes

- The vault path must be a directory your AI tool can read from and write to
- The vault is completely isolated — no links or references to other knowledge bases
- You can have multiple vault paths by creating separate copies of the plugin with different configs
