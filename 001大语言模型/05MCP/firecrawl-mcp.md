## firecrawl

[MCP Registry](https://github.com/mcp)

[MCP Registry | Firecrawl](https://github.com/mcp/firecrawl/firecrawl-mcp-server)

[firecrawl/firecrawl: 🔥 The Web Data API for AI - Turn entire websites into LLM-ready markdown or structured data](https://github.com/firecrawl/firecrawl)

安装本地服务：

npm install -g firecrawl-mcp

Codex 里配置：

将以下firecrawl-mcp的配置更改为codex的配置。

```
{
  "mcpServers": {
    "firecrawl-mcp": {
      "command": "npx",
      "args": ["-y", "firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "fc-b3ff0c8dadc24016b33de6c479159fad"
      }
    }
  }
}
```

codex的配置文件`/Users/Daglas/.codex/config.toml`中有关 mcp 的配置如下，以`zotero-mcp`的配置举例。
```
[mcp_servers.zotero]
command = "zotero-mcp"
args = ["serve"]
env = { ZOTERO_LOCAL = "true" }
```


回复：

```
[mcp_servers.firecrawl]
command = "npx"
args = ["-y", "firecrawl-mcp"]
env = { FIRECRAWL_API_KEY = "fc-b3ff0c8dadc24016b33de6c479159fad" }
```
