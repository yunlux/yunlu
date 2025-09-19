---
{"dg-publish":true,"permalink":"/09/mcp-for-server-developers/","title":"For Server Developers","tags":["网页剪切"],"created":"2025-04-23T15:22:31.319+08:00","updated":"2025-04-23T15:23:01.320+08:00"}
---

In this tutorial, we’ll build a simple MCP weather server and connect it to a host, Claude for Desktop. We’ll start with a basic setup, and then progress to more complex use cases.  
在本教程中，我们将构建一个简单的 MCP 天气服务器并将其连接到主机，Claude for Desktop。我们将从基本设置开始，然后逐步过渡到更复杂的使用案例。

### What we’ll be building 我们将构建的内容

Many LLMs do not currently have the ability to fetch the forecast and severe weather alerts. Let’s use MCP to solve that!  
许多LLMs目前还没有获取预报和严重天气警报的能力。让我们使用 MCP 来解决这个问题！

We’ll build a server that exposes two tools: `get-alerts` and `get-forecast`. Then we’ll connect the server to an MCP host (in this case, Claude for Desktop):  
我们将构建一个服务器，该服务器公开两个工具： `get-alerts` 和 `get-forecast` 。然后我们将服务器连接到 MCP 主机（在这种情况下，是 Claude 桌面版）：

![](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/weather-alerts.png) ![](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/current-weather.png)

Servers can connect to any client. We’ve chosen Claude for Desktop here for simplicity, but we also have guides on [building your own client](https://modelcontextprotocol.io/quickstart/client) as well as a [list of other clients here](https://modelcontextprotocol.io/clients).  
服务器可以连接到任何客户端。在这里我们选择了 Claude 桌面版以简化操作，但我们也有关于构建您自己的客户端以及其他客户端列表的指南。

### Core MCP Concepts 核心 MCP 概念

MCP servers can provide three main types of capabilities:  
MCP 服务器可以提供三种主要功能类型：

1. **Resources**: File-like data that can be read by clients (like API responses or file contents)  
	资源：客户端可以读取的数据（如 API 响应或文件内容）
2. **Tools**: Functions that can be called by the LLM (with user approval)  
	工具：可以由LLM调用（需用户同意）的函数
3. **Prompts**: Pre-written templates that help users accomplish specific tasks  
	提示：帮助用户完成特定任务的预写模板

This tutorial will primarily focus on tools.  
本教程将主要关注工具。

Let’s get started with building our weather server! [You can find the complete code for what we’ll be building here.](https://github.com/modelcontextprotocol/quickstart-resources/tree/main/weather-server-python)  
让我们开始构建我们的天气服务器！您可以在以下链接找到我们将要构建的完整代码。

### Prerequisite knowledge 前置知识

This quickstart assumes you have familiarity with:  
本快速入门假定您熟悉：

- Python
- LLMs like Claude LLMs 类似于 Claude

### System requirements 系统要求

- Python 3.10 or higher installed.  
	Python 3.10 或更高版本已安装。
- You must use the Python MCP SDK 1.2.0 or higher.  
	您必须使用 Python MCP SDK 1.2.0 或更高版本。

### Set up your environment 设置您的环境

First, let’s install `uv` and set up our Python project and environment:  
首先，让我们安装 `uv` 并设置我们的 Python 项目和环境：

Make sure to restart your terminal afterwards to ensure that the `uv` command gets picked up.  
确保之后重启终端，以确保 `uv` 命令被获取。

Now, let’s create and set up our project:  
现在，让我们创建和设置我们的项目：

Now let’s dive into building your server.  
现在让我们深入构建您的服务器。

## Building your server 构建您的服务器

### Importing packages and setting up the instance导入包并设置实例

Add these to the top of your `weather.py`:  
将这些添加到您的 `weather.py` 顶部：

The FastMCP class uses Python type hints and docstrings to automatically generate tool definitions, making it easy to create and maintain MCP tools.  
FastMCP 类使用 Python 类型提示和文档字符串自动生成工具定义，使得创建和维护 MCP 工具变得容易。

### Helper functions 辅助函数

Next, let’s add our helper functions for querying and formatting the data from the National Weather Service API:  
接下来，让我们添加我们的辅助函数，用于查询和格式化国家气象服务 API 的数据：

### Implementing tool execution实现工具执行

The tool execution handler is responsible for actually executing the logic of each tool. Let’s add it:  
工具执行处理器负责实际执行每个工具的逻辑。让我们添加它：

```python
@mcp.tool()
async def get_alerts(state: str) -> str:
    """Get weather alerts for a US state.

    Args:
        state: Two-letter US state code (e.g. CA, NY)
    """
    url = f"{NWS_API_BASE}/alerts/active/area/{state}"
    data = await make_nws_request(url)

    if not data or "features" not in data:
        return "Unable to fetch alerts or no alerts found."

    if not data["features"]:
        return "No active alerts for this state."

    alerts = [format_alert(feature) for feature in data["features"]]
    return "\n---\n".join(alerts)

@mcp.tool()
async def get_forecast(latitude: float, longitude: float) -> str:
    """Get weather forecast for a location.

    Args:
        latitude: Latitude of the location
        longitude: Longitude of the location
    """
    # First get the forecast grid endpoint
    points_url = f"{NWS_API_BASE}/points/{latitude},{longitude}"
    points_data = await make_nws_request(points_url)

    if not points_data:
        return "Unable to fetch forecast data for this location."

    # Get the forecast URL from the points response
    forecast_url = points_data["properties"]["forecast"]
    forecast_data = await make_nws_request(forecast_url)

    if not forecast_data:
        return "Unable to fetch detailed forecast."

    # Format the periods into a readable forecast
    periods = forecast_data["properties"]["periods"]
    forecasts = []
    for period in periods[:5]:  # Only show next 5 periods
        forecast = f"""
{period['name']}:
Temperature: {period['temperature']}°{period['temperatureUnit']}
Wind: {period['windSpeed']} {period['windDirection']}
Forecast: {period['detailedForecast']}
"""
        forecasts.append(forecast)

    return "\n---\n".join(forecasts)
```

### Running the server 运行服务器

Finally, let’s initialize and run the server:  
最后，让我们初始化并运行服务器：

Your server is complete! Run `uv run weather.py` to confirm that everything’s working.  
您的服务器已完成！运行 `uv run weather.py` 以确认一切正常工作。

Let’s now test your server from an existing MCP host, Claude for Desktop.  
现在，让我们从现有的 MCP 主机，Claude for Desktop 测试您的服务器。

## Testing your server with Claude for Desktop使用 Claude for Desktop 测试您的服务器

Claude for Desktop is not yet available on Linux. Linux users can proceed to the [Building a client](https://modelcontextprotocol.io/quickstart/client) tutorial to build an MCP client that connects to the server we just built.  
Claude for Desktop 在 Linux 上尚未提供。Linux 用户可以前往构建客户端教程来构建一个连接到我们刚刚构建的服务器的 MCP 客户端。

First, make sure you have Claude for Desktop installed. [You can install the latest version here.](https://claude.ai/download) If you already have Claude for Desktop, **make sure it’s updated to the latest version.**  
首先，请确保您已安装 Claude for Desktop。您可以从这里安装最新版本。如果您已经安装了 Claude for Desktop，请确保它已更新到最新版本。

We’ll need to configure Claude for Desktop for whichever MCP servers you want to use. To do this, open your Claude for Desktop App configuration at `~/Library/Application Support/Claude/claude_desktop_config.json` in a text editor. Make sure to create the file if it doesn’t exist.  
我们需要配置 Claude for Desktop 以使用您想要的任何 MCP 服务器。为此，请在文本编辑器中打开 Claude for Desktop 应用程序配置文件 `~/Library/Application Support/Claude/claude_desktop_config.json` 。如果文件不存在，请确保创建它。

For example, if you have [VS Code](https://code.visualstudio.com/) installed:  
例如，如果您已安装 VS Code：

You’ll then add your servers in the `mcpServers` key. The MCP UI elements will only show up in Claude for Desktop if at least one server is properly configured.  
然后您将在 `mcpServers` 键中添加您的服务器。如果至少配置了一个服务器，MCP UI 元素将仅在 Claude for Desktop 中显示。

In this case, we’ll add our single weather server like so:  
在这种情况下，我们将这样添加我们的单个天气服务器：

Python

You may need to put the full path to the `uv` executable in the `command` field. You can get this by running `which uv` on MacOS/Linux or `where uv` on Windows.  
您可能需要在 `command` 字段中输入 `uv` 可执行文件的完整路径。您可以通过在 MacOS/Linux 上运行 `which uv` 或在 Windows 上运行 `where uv` 来获取它。

Make sure you pass in the absolute path to your server.  
确保您传递的是服务器的绝对路径。

This tells Claude for Desktop:  
这是对 Claude for Desktop 的说明：

1. There’s an MCP server named “weather”  
	有一个名为“weather”的 MCP 服务器
2. To launch it by running `uv --directory /ABSOLUTE/PATH/TO/PARENT/FOLDER/weather run weather.py`  
	通过运行 `uv --directory /ABSOLUTE/PATH/TO/PARENT/FOLDER/weather run weather.py` 启动它

Save the file, and restart **Claude for Desktop**.  
保存文件，然后重启 Claude for Desktop。

### Test with commands 使用命令进行测试

Let’s make sure Claude for Desktop is picking up the two tools we’ve exposed in our `weather` server. You can do this by looking for the hammer icon:  
确保 Claude for Desktop 正在获取我们在 `weather` 服务器中暴露的两个工具。您可以通过查找锤子 图标来完成此操作：

![](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/visual-indicator-mcp-tools.png)

After clicking on the hammer icon, you should see two tools listed:  
点击锤子图标后，您应该看到列出两个工具：

![](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/available-mcp-tools.png)

If your server isn’t being picked up by Claude for Desktop, proceed to the [Troubleshooting](https://modelcontextprotocol.io/quickstart/server#troubleshooting) section for debugging tips.  
如果您的服务器未被 Claude for Desktop 检测到，请转到故障排除部分以获取调试提示。

If the hammer icon has shown up, you can now test your server by running the following commands in Claude for Desktop:  
如果锤子图标已显示，您现在可以通过在 Claude 桌面版中运行以下命令来测试您的服务器：

- What’s the weather in Sacramento?  
	萨克拉门托的天气怎么样？
- What are the active weather alerts in Texas?  
	德克萨斯州有哪些正在生效的天气警报？
![](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/current-weather.png) ![](https://mintlify.s3.us-west-1.amazonaws.com/mcp/images/weather-alerts.png)

Since this is the US National Weather service, the queries will only work for US locations.  
由于这是美国国家气象服务，查询将仅适用于美国地区。

## What’s happening under the hood发生在引擎盖下的是什么？

When you ask a question:  
当你提出一个问题时：

1. The client sends your question to Claude  
	客户将你的问题发送给 Claude
2. Claude analyzes the available tools and decides which one(s) to use  
	克劳德分析可用的工具并决定使用哪个（些）
3. The client executes the chosen tool(s) through the MCP server  
	客户端通过 MCP 服务器执行所选的工具（们）
4. The results are sent back to Claude  
	结果被发送回克劳德
5. Claude formulates a natural language response  
	克劳德制定自然语言响应
6. The response is displayed to you!  
	响应已显示给您！

## Troubleshooting 故障排除

For more advanced troubleshooting, check out our guide on [Debugging MCP](https://modelcontextprotocol.io/docs/tools/debugging)  
为了更高级的故障排除，请查看我们的调试 MCP 指南## [Building a client 构建客户端](https://modelcontextprotocol.io/quickstart/client)

[

Learn how to build your own MCP client that can connect to your server  
学习如何构建自己的 MCP 客户端，以便连接到您的服务器

](https://modelcontextprotocol.io/quickstart/client)Example servers 服务器示例

Check out our gallery of official MCP servers and implementations  
查看我们的官方 MCP 服务器和实现示例库

[View original](https://modelcontextprotocol.io/examples)Debugging Guide 调试指南

Learn how to effectively debug MCP servers and integrations  
学习如何有效地调试 MCP 服务器和集成

[View original](https://modelcontextprotocol.io/docs/tools/debugging)Building MCP with LLMs 使用LLMs构建 MCP

Learn how to use LLMs like Claude to speed up your MCP development  
学习如何像 Claude 一样使用LLMs来加速你的 MCP 开发

[View original](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms)