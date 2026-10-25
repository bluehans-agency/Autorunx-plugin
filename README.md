<p align="center"><img src="assets/logo.png" width="96" alt="AutorunX logo"></p>

# AutorunX for coding agents

Make AI films, pictures and music on [AutorunX](https://autorunx.com) from Claude Code, Codex,
Cursor or any MCP client. Your agent plans the film; AutorunX makes it. Everything lands in a
Studio Mix project on autorunx.com that you can open and edit.

- **Video** runs on your own rented GPU on AutorunX (Rent GPU).
- **Pictures and music** use AutorunX cloud models, paid from your credits.
- Needs a paid AutorunX plan (Starter or Pro).

## 1. Get an API key

On [autorunx.com](https://autorunx.com): profile picture → **API keys** → **New key**.
It starts with `axk_` and is shown once.

## 2. Connect your agent

### Claude Code (plugin)

```bash
/plugin marketplace add bluehans-agency/Autorunx-plugin
/plugin install autorunx@autorunx
```

Claude Code asks for your API key and stores it in your system keychain.

Or add only the MCP server:

```bash
claude mcp add --transport http autorunx https://autorunx.com/api/mcp \
  --header "Authorization: Bearer axk_YOUR_KEY"
```

### Codex

```bash
codex plugin marketplace add bluehans-agency/Autorunx-plugin
```

Or add only the MCP server to `~/.codex/config.toml`:

```toml
[mcp_servers.autorunx]
url = "https://autorunx.com/api/mcp"
http_headers = { Authorization = "Bearer axk_YOUR_KEY" }
```

### Cursor, Windsurf, VS Code and other MCP clients

```json
{
  "mcpServers": {
    "autorunx": {
      "url": "https://autorunx.com/api/mcp",
      "headers": { "Authorization": "Bearer axk_YOUR_KEY" }
    }
  }
}
```

## 3. Ask for a film

> Make a 30-second film about a lighthouse keeper's last night, with music.

## Tools

| Tool                                                   | What it does                                                                             |
| ------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| `list_models`                                          | Your running GPUs and their video models, cloud picture and music models, credit balance |
| `create_project` / `list_projects` / `get_project`     | Studio Mix projects                                                                      |
| `submit_plan` / `start_item`                           | Send a whole film plan; start its items                                                  |
| `generate_video` / `generate_image` / `generate_music` | Make one clip, picture or song                                                           |
| `get_job`                                              | Progress and the finished file                                                           |
| `upload_reference`                                     | Upload your own picture to use as a frame                                                |
| `get_storyboard` / `set_storyboard`                    | Read and change the storyboard                                                           |
| `get_script` / `set_script`                            | Read and change each item's script                                                       |
| `set_prompt`                                           | The project's prompt box                                                                 |
| `post_to_thread`                                       | Leave a card in the project's chat                                                       |
| `get_timeline` / `edit_timeline`                       | Add, move, trim and remove clips on the timeline                                         |

Every change saves a checkpoint first, so you can undo it on autorunx.com.

## Help

- Support: [support@autorunx.com](mailto:support@autorunx.com)
- [Privacy policy](https://autorunx.com/privacy) · [Terms](https://autorunx.com/terms)

## License

MIT (this plugin's files). AutorunX itself is a paid service.
