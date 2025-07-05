[Zotero MCP | Your Research Library in Claude](https://stevenyuyy.us/zotero-mcp/)

### 提示词

在zotero中搜索与machine learning相关的论文

#### 原始提示词

Search Tools
zotero_search_items: Search your library
zotero_advanced_search: Perform complex searches
zotero_get_collections: List collections
zotero_get_collection_items: Get items in a collection
zotero_get_tags: List all tags
zotero_get_recent: Get recently added items
zotero_search_by_tag: Search your library using custom tag filters
Content Tools
zotero_get_item_metadata: Get detailed metadata
zotero_get_item_fulltext: Get full text content
zotero_get_item_children: Get attachments and notes
Annotation & Notes Tools
zotero_get_annotations: Get annotations (including direct PDF extraction)
zotero_get_notes: Retrieve notes from your Zotero library
zotero_search_notes: Search in notes and annotations (including PDF-extracted)
zotero_create_note: Create a new note for an item (beta feature)

#### Claude 里的提示词

Example prompts:
"Search my library for papers on machine learning"
"Find recent articles I've added about climate change"
"Summarize the key findings from my paper on quantum computing"
"Extract all PDF annotations from my paper on neural networks"
"Search my notes and annotations for mentions of 'reinforcement learning'"
"Create a detailed note for my climate paper with a summary of key points"


在 Claude 客户端里输入 /tools zotero 后得到的回复：

I can help you work with your Zotero library! Here are the Zotero tools I have available:

\## Search & Discovery
- **Search items** - Find items by title, author, year, or full text
- **Search by tags** - Find items with specific tags (supports AND/OR logic)
- **Advanced search** - Complex searches with multiple criteria
- **Get recent items** - See your most recently added items

\## Library Organization
- **List collections** - View all your collections
- **Get collection items** - See items in a specific collection
- **Get all tags** - View all tags in your library

\## Item Details
- **Get item metadata** - Full bibliographic details and abstracts
- **Get item full text** - Complete text content of PDFs
- **Get item children** - Attachments and notes for an item

\## Notes & Annotations
- **Get notes** - Retrieve notes from items
- **Search notes** - Find notes by content
- **Create notes** - Add new notes to items
- **Get annotations** - View highlights and annotations

\## Bulk Operations
- **Batch update tags** - Add/remove tags across multiple items

What would you like to do with your Zotero library? I can help you search for specific papers, organize your collection, work with notes and annotations, or perform any other Zotero-related tasks.

### 配置

#### Claude 客户端里配置

先安装：

[54yyyu/zotero-mcp: Zotero MCP: Connects your Zotero research library with Claude and other AI assistants via the Model Context Protocol to discuss papers, get summaries, analyze citations, and more.](https://github.com/54yyyu/zotero-mcp?tab=readme-ov-file)

```
uv tool install "git+https://github.com/54yyyu/zotero-mcp.git"
```

再配置：

```
zotero-mcp setup  # Auto-configure for ### 01 Desktop
```

配置完成后的信息：

Using arguments passed from command line
Found zotero-mcp in PATH at: /Users/Daglas/.local/bin/zotero-mcp
Using zotero-mcp at: /Users/Daglas/.local/bin/zotero-mcp
Found Claude Desktop config at: /Users/Daglas/Library/Application Support/Claude/claude_desktop_config.json

Setup with the following settings:
  Local API: True
Loaded existing config from: /Users/Daglas/Library/Application Support/Claude/claude_desktop_config.json

Successfully wrote config to: /Users/Daglas/Library/Application Support/Claude/claude_desktop_config.json

Setup complete!
To use Zotero in Claude Desktop:
1. Restart Claude Desktop if it's running
2. In Claude, type: /tools zotero

Note: Make sure Zotero desktop is running and the local API is enabled in preferences.

\### shiys

#### cursor 里配置

cursor 中的配置：

{
  "mcpServers": {
    "zotero": {
      "command": "zotero-mcp",
      "env": {
        "ZOTERO_LOCAL": "true"
      }
    }
  }
}
