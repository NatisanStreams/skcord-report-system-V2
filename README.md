# SkCord Report System

A lightweight Skript-based player report system for Minecraft servers that sends reports directly to a Discord channel via webhooks using [SkCord](https://github.com/Olyno/SkCord).

## Features

- `/report` command with configurable reasons
- Discord webhook integration — reports appear as rich embeds with reporter, accused player, reason, and a unique tracking code
- Auto-generated alphanumeric report codes players can copy and use to open a ticket
- Fully configurable via YAML (prefix, permissions, reasons list, webhook URL, code length)
- Config reload command for admins
- Tab completion for report reasons and admin subcommands

## Requirements

- [Skript](https://github.com/SkriptLang/Skript)
- [SkBee](https://github.com/ShaneBeee/SkBee)
- [SkCord](https://github.com/feeeedox/skCord-v3)
- [skript-yaml](https://github.com/Sashie/skript-yaml)

## Installation

1. Drop the `.sk` file into your `plugins/Skript/scripts/` folder.
2. Restart the server or run `/skript reload <filename>`.
3. A config file will be generated at `plugins/SkCord-Report-System/config.yml` on first load.
4. Open the config and paste your Discord webhook URL into `config.webhook-link`.
5. Reload the config with `/report reloadconfig`.

## Configuration

The config is generated automatically with sensible defaults. Here's what you can customise:

| Key | Default | Description |
|---|---|---|
| `config.webhook-link` | `WEBHOOK-LINK-GOES-HERE` | Your Discord channel webhook URL |
| `config.prefix` | `&f[&cREPORT&f]` | Chat prefix shown in-game |
| `config.permission` | `ers.report` | Permission node to use `/report` |
| `config.permission-message` | `You have been blacklisted from using the report system` | Message shown when a player lacks permission |
| `config.admin-permission` | `ers.admin` | Permission node for `/report reloadconfig` |
| `config.code-numerical-value` | `6` | Length of the generated report code |
| `reasons` | `Cheating`, `X-Ray`, `Chat Conduct` | List of selectable report reasons |

## Usage

### Reporting a Player

```
/report <player> <reason>
```

The player will receive a unique report code they can click to copy, which can be used to reference the report when opening a support ticket.

### Reloading the Config

```
/report reloadconfig
```

Requires the admin permission defined in your config.

## Discord Embed

When a report is submitted, a webhook message is sent to your configured Discord channel containing:

- **Reporter** — who filed the report
- **Reported** — the accused player
- **Reason** — the selected reason
- **Code** — the unique tracking code

## License

Feel free to use and modify this for your own server. Credit appreciated but not required.
