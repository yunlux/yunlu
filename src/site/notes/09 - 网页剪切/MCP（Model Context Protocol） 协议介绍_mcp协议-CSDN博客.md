---
{"dg-publish":true,"permalink":"/09 - 网页剪切/MCP（Model Context Protocol） 协议介绍_mcp协议-CSDN博客/","title":"MCP（Model Context Protocol） 协议介绍_mcp协议-CSDN博客","tags":["网页剪切"],"created":"2025-03-18T00:17:12.296+08:00","updated":"2025-03-18T00:51:57.999+08:00"}
---

更多新鲜技术资讯，欢迎关注公众号： [Linux开源先锋](https://mp.weixin.qq.com/s/Howw39n8qpbvLFoOqJ5NtQ)

更多开源技术，请关注以上公众号

| 缩写 | 全称 | 描述 |
| --- | --- | --- |
| Anthropic | / | 一家 AI 公司，推出了 Claude 3.5 Sonnet 模型 |
| MCP | Model Context Protocol | 模型上下文协议，LLM 应用程序和外部数据源之间无缝集成的协议 |
| uv | / | 一个快速的 Python 包和项目管理器，用 Rust 编写。 |

## MCP 介绍

### 概要

模型上下文协议 (MCP) 是一种开放协议，可实现 LLM 应用程序与外部[数据源](https://so.csdn.net/so/search?q=%E6%95%B0%E6%8D%AE%E6%BA%90&spm=1001.2101.3001.7020)和工具之间的无缝集成，无论是构建智能 IDE、扩展接口，还是创建 AI 工作流程，MCP 都提供了一种标准化方法，将 LLMs 与其所需的上下文连接起来。![MCP调用流程](https://i-blog.csdnimg.cn/direct/7e951db364804da6a6016873d00f790a.png)  
如上图所示，其中每个节点的作用如下：

- **MCP Hosts**: 通过 MCP 访问资源的程序，例如 Claude Desktop、IDE 或 AI 工具。
- **MCP Clients**: 与服务器保持 1:1 连接的协议客户端。
- **MCP Servers**: 每个轻量级程序都通过标准化模型上下文协议公开特定功能
- **Local Resources**: MCP 服务器可以安全访问的计算机资源（数据库、文件、服务）
- **Remote Resources**: MCP 服务器可以连接到的互联网上可用的资源（例如，通过 API）

可以看到，其中最主要的部分是 MCPServer，这是一个实现了本地资源或者远端资源交互的程序，并且实现 MCP 协议。  
Host 去调用资源时，实际上是通过不同的 MCPServer 去调用，比如 Server 可以是 GitHub 相关，也可以是 sqlite 相关。  
例如，通过 MCP 去访问本地的数据库，具体流程如下：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5ed854c2a9af476da71cbe047a823c63.png)

- Claude Desktop 充当 MCP 客户端
- SQLite MCP Server 提供安全的数据库访问
- 本地 SQLite 数据库存储实际数据

Server 和本地 SQLite 数据库之间的通信完全发生在本地，MCP 确保 Claude Desktop 只能通过明确定义的接口执行批准的数据库操作，所以这是一种安全的方式让 Claude 分析本地数据并与之交互，同时保持对其可以访问的内容的完全控制。

通过该实例进行发散，如果要通过 MCP 访问更多的外部数据，就需要添加无数个 MCPServer。  
这种添加方式就类似于增加插件，那么现在 MCP 的能力就受限于 MCPServer 的个数。

### 原理

当使用 MCP 与 Claude Desktop 交互时，具体流程如下：

1.**Server Discovery**:  
Claude Desktop 在启动时连接到配置好的 MCP 服务器

2.**Protocol Handshake**:  
当询问数据时，Claude Desktop：

- 确定哪个 MCP 服务器可以提供帮助（在本例中为 sqlite）
- 通过协议协商能力
- 从 MCP 服务器请求数据或操作

3.**Interaction Flow**:  
![请添加图片描述](https://i-blog.csdnimg.cn/direct/bbddd595fcd144ddbfe60a0f4ab423fe.png)  
4.**Security**:

- MCP 服务器仅公开特定的、受控的功能
- MCP 服务器在本地运行，它们访问的资源不会暴露在互联网上
- 需要用户确认敏感操作

不过这也有一个问题，MCPServer 是如何部署到本地的呢？如果一开始就集成到安装包里面，那后续要扩展，是否需要动态从仓库中下载？

## 已有的 MCPServer

在官方给出的仓库里面，已经包含了 10 余种 Server，包括 git、github、sqlite 等，不过目前来看，数量还是比较少的。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/bc61be89b6cf438badd704f1cf1dc8d9.png)

所以理论上，如果要获取更多服务，还是要面向自己的业务编写 Server。

## 如何创建自己的 MCPServer

以下是用 Python 生成一个 MCPServer 的示例，总体来说还是比较方便。

### 前置工作

1、创建工程  
MCP 已经提供了工程创建器，所以我们不用从零开始写代码。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7d28bf3f6ad34f199486b8cd374c23c6.png)  
这里是用的 uv 包管理器，可以通过“create-mcp-server”直接创建模板工程。

2、创建环境  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/6d1ca3cd5dd84d4ca1e89ad78b4abf9f.png)  
这里需要创建一个访问服务的 Key。  
*说明：当我们要访问的服务需要验证，就需要添加访问 Key。*

### 创建服务

在模板 weather\_service/src/weather\_service/server.py 文件中，添加具体代码。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8af99e96641542f5833337de7e9b90df.png)

后续只要实现 MCP 的具体接口即可。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e4672bec5e924d27aeeb2ce97a013d2f.png)

## 总结

MCP 是一个全新的协议，在 AI 领域也需要一个统一的协议去抽象不同工具、数据的调用，MCP 如果能继续发展完善，将有可能成为 AI 领域的 LSP。

此外，对工具的调用，让我们容易想到另一种方式----Function Call，以下是它和 MCP 使用建议：

- 对于需要复杂上下文管理的场景，优先考虑 MCP
- 对于需要明确功能调用的场景，继续使用 Function Call
- 在大型项目中考虑两者结合使用

目前来看，可以将 MCP、FunctionCall、视觉驱动三者结合起来，进而增大 AI 的交互边界，为用户带来更便捷的体验。

更多新鲜技术资讯，欢迎关注公众号： [Linux开源先锋](https://mp.weixin.qq.com/s/Howw39n8qpbvLFoOqJ5NtQ)

## 参考

[uv](https://docs.astral.sh/uv/)  
[MCP GitHub](https://github.com/modelcontextprotocol)  
[MCPServer 仓库](https://github.com/modelcontextprotocol/servers/tree/main/src)  
[MCPServer 创建指南](https://modelcontextprotocol.io/docs/first-server/python)