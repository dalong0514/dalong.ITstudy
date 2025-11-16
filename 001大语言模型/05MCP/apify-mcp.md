## apify

[MCP Registry](https://github.com/mcp)

[MCP Registry | Apify](https://github.com/mcp/apify/apify-mcp-server#-quickstart)

[Apify MCP server | Platform | Apify Documentation](https://docs.apify.com/platform/integrations/mcp)

Codex安装apify-mcp

在文件/Users/Daglas/.codex/config.toml里添加如下信息。

```
[mcp_servers.apify]
url = "https://mcp.apify.com?tools=actors,docs,apify/rag-web-browser"
```

在配置文件的最后加上如下信息，否则没法做网页登录验证。

```
[features]
rmcp_client = true
```

ClaudeCode安装apify

远程版：
claude mcp add --transport http apify https://mcp.apify.com


本地没跑通，因为要求 node 版本必须要 20+ 才可以，之前自己因为一直用的 node 18，懒得更换了，改用远程端的 mcp。

npx -y @apify/actors-mcp-server --actors apify/instagram-scraper,apify/rag-web-browser

claude mcp add --transport stdio apify-local "npx -y @apify/actors-mcp-server --actors apify/instagram-scraper,apify/rag-web-browser" --env APIFY_TOKEN=YOUR_TOKEN