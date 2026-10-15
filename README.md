# SchemaBounce plugins for Claude Code

The SchemaBounce plugin marketplace. Add it once, then install plugins by
name and receive releases with `claude plugin update`.

```
/plugin marketplace add SchemaBounce/claude-plugins
/plugin install schemabounce@schemabounce
```

Or both in one command from a shell: `claude plugin install schemabounce --marketplace SchemaBounce/claude-plugins`.

## Plugins

| Install id | What it does | Source |
|---|---|---|
| `schemabounce@schemabounce` | Finds the SchemaBounce decision records that govern the files you are changing, cites them, and proposes new ones without ratifying. A skill, a pre-edit hook and the hosted SchemaBounce MCP. | [SchemaBounce/schemabounce-agent-kit](https://github.com/SchemaBounce/schemabounce-agent-kit), pinned to a release tag |

Each entry points at a release tag of the plugin's own repository, so what
you install is a reviewed release, never a branch head. The plugin
repository's own marketplace entry (`schemabounce@schemabounce-agent-kit`)
tracks its development branch and is for people working on the plugin.

## Enable for everyone in a repository

Check this into the repository's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "schemabounce": {
      "source": { "source": "github", "repo": "SchemaBounce/claude-plugins" }
    }
  },
  "enabledPlugins": {
    "schemabounce@schemabounce": true
  }
}
```

## Releases

A plugin release is a version bump in its `plugin.json`, an immutable git tag
`<plugin>--v<version>` on the plugin repository, and a GitHub release there
with a zip of the plugin folder and its sha256. This catalog moves an entry's
`ref` to the new tag. Users on auto-update receive it; others run
`claude plugin update schemabounce@schemabounce`.

## Security

This repository is a catalog: one JSON file and this README, no code. Every
plugin it lists carries its own README that says what it runs, sends and
fetches, and its own license. The hosted SchemaBounce MCP needs each person's
own sign-in; nothing here holds a credential.

## License

Apache-2.0. Each listed plugin carries its own license.
