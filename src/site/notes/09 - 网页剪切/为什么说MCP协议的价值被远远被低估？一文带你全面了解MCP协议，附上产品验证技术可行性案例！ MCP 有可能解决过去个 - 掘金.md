---
{"dg-publish":true,"permalink":"/09 - 网页剪切/为什么说MCP协议的价值被远远被低估？一文带你全面了解MCP协议，附上产品验证技术可行性案例！ MCP 有可能解决过去个 - 掘金/","title":"为什么说MCP协议的价值被远远被低估？一文带你全面了解MCP协议，附上产品验证技术可行性案例！ MCP 有可能解决过去个 - 掘金","tags":["网页剪切"]}
---

[极客见识](https://juejin.cn/user/3305544549144932/posts)

![](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/img/banner.a5c9f88.jpg)

2024年11月25日，Claude 公司提出并开源的一项新标准协议 MCP，我觉着这是一件很重要的大事，关注的人却不多，它的价值被大家远远低估了。

因为 MCP 有可能解决过去个人电脑、企业、互联网数据割裂，互为信息孤岛的局面，迎来一个多系统互联互操作的繁荣生态。

价值很大很大！文章后面有彩蛋喔！

这篇文章试着带大家从 MCP 是什么、价值、与 Function Calling 的区别、数据安全以及工作原理，让大家更全面了解 MCP 的潜在价值。

![image.png](https://p3-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/c08b0ef11f9444b8ade1124e0221f2c3~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5p6B5a6i6KeB6K-G:q75.awebp?rk3s=f64ab15b&x-expires=1742390621&x-signature=DCsT%2Bc0nyg%2BD1j%2BPZH3K8d8Fvpk%3D)

**01 什么是 MCP**

官方是这样介绍的：

MCP 是一种开放标准，可让开发人员在其数据源和 AI 驱动的工具之间建立安全的双向连接。该架构非常简单：开发人员可以通过 MCP 服务器公开其数据，也可以构建连接到这些服务器的 AI 应用程序（MCP 客户端）。

简单来说，就是开发者能够借助“MCP 服务器”把数据共享出来，然后开发出应用程序、工作流之类的“MCP 客户端”，通过命令对各类数据源进行访问。使用这个标准协议，我们就无需为每个数据源单独维护连接器，从而使生态系统更加互联。

**02 MCP 的价值**

在过去，为了让大模型等 AI 应用使用我们的数据，要么复制粘贴，要么上传下载，非常麻烦。

即使是最强大模型也会受到数据隔离的限制，形成信息孤岛，要做出更强大的模型，每个新数据源都需要自己重新定制实现，使真正互联的系统难以扩展，存在很多的局限性。

现在，MCP 可以直接在 AI 与数据（包括本地数据和互联网数据）之间架起一座桥梁，通过 MCP 服务器和 MCP 客户端，大家只要都遵循这套协议，就能实现“万物互联”。

我们在细品一下。

是不是只要我们都把数据暴露出来，AI 就能够更充分地利用外部数据，从而拓展模型能力，生成更精准、更有针对性的响应。

只要大家共同来构建这套协议，MCP 将推动整个 AI 生态系统和其他应用系统互相操作的快速发展。

但能操作空间远不止于此，留给大家自己头脑风暴。

顺便提一嘴，是不是我们在打造产品时，应该好好预测一下 AI 的未来能力，不要去解决即将消失的问题。（也就是我们现在打造的引以为傲的技术能力，在未来，AI 就能取代。）

**03 MCP 与 Function Calling 的区别**

\- MCP（Model Context Protocol），模型上下文协议

\- Function Calling，函数调用

这两种技术都旨在增强 AI 模型与外部数据的交互能力，但 MCP 不止可以增强 AI 模型，还可以时其他的应用系统。

![image.png](https://p3-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/0b0989ecdfa54ca996f0fcecb2afa2df~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5p6B5a6i6KeB6K-G:q75.awebp?rk3s=f64ab15b&x-expires=1742390621&x-signature=PVyV%2BbEKN3xNlMEHXOeGKgEMnkM%3D)

**MCP（Model Context Protocol）：**

MCP 协议是由 Anthropic 提出的，一种更为高级和灵活的交互范式，MCP 被设计为一个开放的、标准化的协议，它不仅支持 AI 模型与单个数据源或功能连接，还能实现与多个不同的数据源和服务之间的无缝集成。

通过 MCP，AI 模型能够以更自然的方式与外部世界进行交互，无需为每种数据类型或服务编写专门的接口。这种“即插即用”的特性极大地提高了AI应用的灵活性和扩展性。

**Function Calling：**

Function Calling 是由 OpenAI 提出，是一种直接且明确的方法，它允许开发者以 JSON 格式向特定的 AI 模型（GPT-4o）描述特定的函数，并在生成响应前由模型判断是否需要调用这些函数。

这种方法的优势在于其直观性和易理解性，特别适用于处理简单、单一任务的场景，如查询天气或执行翻译等。不过，这种方式的缺点也很明显，即为每个新任务或数据源开发单独的函数可能会增加开发和维护的复杂度。

**举个栗子：**

我现在想要让大模型自动帮我把代码推送到 GitHub上。

我就需要自定义一个函数，实现对 GitHub API 的调用，然后将函数转化成 OpenAI 的格式，然后解析 OpenAI 规范返回的值，最后执行这个函数。

也就是说，没有MCP协议，我们需要：

- **自己编写函数：** 编写一个函数来实现与GitHub API的交互。
- **转换格式：** 将这个函数转换成大模型能理解的格式。
- \*\*解析结果：\*\*接收模型返回的函数调用信息，并解析其中的参数。
- **执行函数：** 根据解析结果，调用你之前编写的函数。

整个过程中的每个环节都需要我们手动处理，你就说累不累吧。

现在，有了 MCP 协议，这个问题就解决了。

MCP 提供了一套标准化的方式，让大模型可以轻松地与各种服务进行交互。

我们只需要：

- **使用 MCP 客户端：** 在你的应用程序（比如前端页面）中使用MCP提供的客户端SDK。
- **调用 MCP 服务端：** 服务端（比如GitHub）也需要使用MCP提供的服务端SDK。

一旦双方都遵循了 MCP 协议，大家通过 MCP Server 把数据暴露出来，我们就可以直接在应用程序中调用世界上所有的数据，就像调用本地函数一样方便。

说到这里，大家是不是觉得 Function Calling 就没有用了。

其实，还是要看我们自己的需求，如果是想给模型增加一些简单的“增值服务”，解决特定任务，Function Calling 是一个更好的选择，如果想做一个数据、功能更灵活可互操作系统/应用，MCP 则是操作空间更大。

**04  数据安全性**

这样一个理想的“万物互联”生态系统看着很让人着迷。

但，大家是不是担心通过 MCP Server 暴露出来的数据会泄露或被非法访问，这个头疼的问题 MCP 也考虑到了。

MCP 通过标准化的数据访问接口，大大减少了直接接触敏感数据的环节，降低了数据泄露的风险。

还有，MCP 内置了安全机制，确保只有经过验证的请求才能访问特定资源，相当于在数据安全又加上了一道防线。同时，MCP协议还支持多种加密算法，以确保数据在传输过程中的安全性。

例如，MCP 服务器自己控制资源，不需要将 API 密钥等敏感信息提供给 LLM 提供商。这样一来，即使 LLM 提供商受到攻击，攻击者也无法获取到这些敏感信息。

不过，MCP 这套协议/标准，需要大家一起来共建，这个生态才会繁荣，现在，只是测试阶段，一切才刚刚开始，当然，还会涌现出更多的问题。

**05 MCP 的工作原理**

MCP 协议采用了一种独特的架构设计，它将 LLM 与资源之间的通信划分为三个主要部分：客户端、服务器和资源。

客户端负责发送请求给 MCP 服务器，服务器则将这些请求转发给相应的资源。这种分层的设计使得 MCP 协议能够更好地控制访问权限，确保只有经过授权的用户才能访问特定的资源。

**以下是 MCP 的基本工作流程：**

- \*\*初始化连接：\*\*客户端向服务器发送连接请求，建立通信通道。
- \*\*发送请求：\*\*客户端根据需求构建请求消息，并发送给服务器。
- \*\*处理请求：\*\*服务器接收到请求后，解析请求内容，执行相应的操作（如查询数据库、读取文件等）。
- \*\*返回结果：\*\*服务器将处理结果封装成响应消息，发送回客户端。
- \*\*断开连接：\*\*任务完成后，客户端可以主动关闭连接或等待服务器超时关闭。

![image.png](https://p3-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/aa771f7da39242a8a321c84b2b7c0dc1~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5p6B5a6i6KeB6K-G:q75.awebp?rk3s=f64ab15b&x-expires=1742390621&x-signature=pMfXofgZRTWIRy7rv2jwEfQ4NqY%3D)

**1、核心架构**

MCP协议遵循客户端-服务器架构，其中包含三个主要组件：

- \*\*MCP Host：\*\*这是运行Claude Desktop、IDE或其他AI工具的应用程序，作为MCP协议的客户端。
- \*\*MCP Client：\*\*负责与MCP Server保持一对一的连接，处理实际的数据传输和命令执行。
- \*\*MCP Server：\*\*提供对本地或远程资源的访问能力，实现具体的功能或服务。

**2、通信机制**

MCP 协议支持两种主要的通信机制：基于标准输入输出的本地通信和基于SSE（Server-Sent Events）的远程通信。

这两种机制都使用 JSON-RPC 2.0 格式进行消息传输，确保了通信的标准化和可扩展性。

- \*\*本地通信：\*\*通过 stdio 传输数据，适用于在同一台机器上运行的客户端和服务器之间的通信。
- \*\*远程通信：\*\*利用 SSE 与 HTTP 结合，实现跨网络的实时数据传输，适用于需要访问远程资源或分布式部署的场景。

**3、消息类型**

MCP定义了4类消息类型，以支持复杂的交互流程。

- Requests（请求）
- Results（结果）
- Errors（错误）
- Notifications（通知）

**彩蛋时刻**

这个 MCP 说得天花乱坠，也需要有产品落地来验证技术得可行性，那才算有说服力。

所以，我跟技术大佬 idoubi 交流之后，并得到允可，给大家展示一下基于 MCP 协议做的群聊总结产品，让大家亲身感受落地场景。

> By idoubi
> 
> 2024年12月4日

我去年写了一个叫 ChatSum 的群聊总结工具，用 wechaty 框架实时收集微信消息，在群里@机器人提问，请求大模型 API，总结群聊话题。

当时的方案是在提问时拿到群聊消息发给 Claude2 总结，会有隐私问题，也受到了 Claude 模型长度的限制，总结效果不太好，后面这个项目就搁置了。

上周 Anthropic 发布 MCP 协议之后，我打算把这个项目捡起来，技术方案调整了一下：

1. 用 wechaty 在自己电脑上运行微信机器人，实时收集微信消息，存储在本地文件。
2. 在自己电脑运行一个 mcp-server-chatsum 程序，接收查询请求，从本地文件返回匹配的微信消息（根据群名/联系人/话题组合查询）。
3. 使用 Claude 桌面版作为交互入口，随时查询和总结微信消息，由 Claude 桌面版与本地的 mcp-server-chatsum 进程通行，再由 Claude 内置的大模型完成总结回复。

比如我可以这么问：

- 今天早上大家都在聊啥？
- 关于 MCP 最近有哪些讨论？
- idoubi 在哪些群分享了什么内容？
- AI-Native 群最活跃的5个用户和关心的话题是什么？

![image.png](https://p3-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/8235d96020db424495c7828db424f2cf~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5p6B5a6i6KeB6K-G:q75.awebp?rk3s=f64ab15b&x-expires=1742390621&x-signature=hx3UkrU0ldlR62UfIkmf7Xr29Js%3D)

比起去年的实现方案，用 MCP Server 来实现 ChatSum 的功能有一些不同点：

- 消息存储和查询总结完全解耦，灵活性更高。
- 由 Claude 客户端做服务发现/意图识别/参数提取 / 流程串联等步骤，准确性更高（之前用的是 Function Calling)。
- 虽然现在交互入口用的是 Claude 桌面版，按照 MCP 协议的约定，后面可以自己实现一个 MCP Client，调用本地的大模型，实现完全私有化，数据安全性更高。

MCP Client 作为个人电脑的超级入口，AI 助理 2.0 时代即将到来。

微信机器人和消息总结 MCP Server 代码已开源。

GitHub 地址：

[github.com/chatmcp/mcp…](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fchatmcp%2Fmcp-server-chatsum "https://github.com/chatmcp/mcp-server-chatsum")

欢迎大家自行部署体验。

![image.png](https://p3-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/55d725f41db3480d9d564e7d74f2874b~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5p6B5a6i6KeB6K-G:q75.awebp?rk3s=f64ab15b&x-expires=1742390621&x-signature=w7KHTNjdQukp%2FyJzgqeNcxV5o1k%3D)

**Last but not least**

MCP 协议重新定义了各个生态系统之间互联的一个新风向标，解决了过去个人电脑、企业、互联网之间互为信息孤岛的问题，让全世界的数据割裂局面有可能变成一个欣欣向荣的繁荣生态。

这个理想很美好，实现也非常难，但 Anthropic 给我们起了一个好头，让我们看到了更多的未来！

Respect !

Claude 官方文档：

[www.anthropic.com/news/model-…](https://link.juejin.cn/?target=https%3A%2F%2Fwww.anthropic.com%2Fnews%2Fmodel-context-protocol "https://www.anthropic.com/news/model-context-protocol")

---

往期精彩文章推荐：

1.[2025，AI Agents和AI玩具谁先会爆发呢？](https://link.juejin.cn/?target=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkyNDYwMzg3OA%3D%3D%26mid%3D2247488875%26idx%3D1%26sn%3D42c011b61a5d7f01cae68d13343685b1%26scene%3D21%23wechat_redirect "https://mp.weixin.qq.com/s?__biz=MzkyNDYwMzg3OA==&mid=2247488875&idx=1&sn=42c011b61a5d7f01cae68d13343685b1&scene=21#wechat_redirect")

[2.OpenAI CEO Sam Altman 2024年终总结丨反思](https://link.juejin.cn/?target=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkyNDYwMzg3OA%3D%3D%26mid%3D2247488886%26idx%3D1%26sn%3D868656be2540991435200cb37bae8cae%26scene%3D21%23wechat_redirect "https://mp.weixin.qq.com/s?__biz=MzkyNDYwMzg3OA==&mid=2247488886&idx=1&sn=868656be2540991435200cb37bae8cae&scene=21#wechat_redirect")

[3.英伟达重磅发布RTX5090，AI、AI还是AI！](https://link.juejin.cn/?target=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkyNDYwMzg3OA%3D%3D%26mid%3D2247488934%26idx%3D1%26sn%3D0ea0df5b407f2e0a9e6e8a7bee621c96%26scene%3D21%23wechat_redirect "https://mp.weixin.qq.com/s?__biz=MzkyNDYwMzg3OA==&mid=2247488934&idx=1&sn=0ea0df5b407f2e0a9e6e8a7bee621c96&scene=21#wechat_redirect")