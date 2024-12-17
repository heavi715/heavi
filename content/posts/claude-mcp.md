+++
title = 'AI Claude MCP'
date = 2024-11-02T15:45:51+08:00
draft = true
+++

# claude MCP (model context protocol)

<https://github.com/modelcontextprotocol/servers>

模型上下文协议 （MCP） 是一种开放协议，可实现 LLM 应用程序与外部数据源和工具之间的无缝集成。无论您是构建 AI 驱动的 IDE、增强聊天界面，还是创建自定义 AI 工作流，MCP 都提供了一种标准化的方式来将 LLMs 与它们所需的上下文连接起来。

<https://modelcontextprotocol.io/quickstart>

通过claude 客户端
![alt text](https://heavi.cn/posts/claude-mcp/image.png)

```
code ~/Library/Application\ Support/Claude/claude_desktop_config.json

{
  "mcpServers": {
    "sqlite": {
      "command": "uvx",
      "args": ["mcp-server-sqlite", "--db-path", "/Users/YOUR_USERNAME/test.db"]
    }
  }
}
```

![img](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/quickstart-screenshot.png)