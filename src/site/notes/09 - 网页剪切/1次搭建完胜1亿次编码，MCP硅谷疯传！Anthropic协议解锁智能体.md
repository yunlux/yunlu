---
{"dg-publish":true,"permalink":"/09 - 网页剪切/1次搭建完胜1亿次编码，MCP硅谷疯传！Anthropic协议解锁智能体/","title":"1次搭建完胜1亿次编码，MCP硅谷疯传！Anthropic协议解锁智能体","tags":["网页剪切"]}
---

[百度首页](https://www.baidu.com/)

[如讷x](http://i.baidu.com/)

[个人中心](http://i.baidu.com/center)[帐号设置](http://passport.baidu.com/)[意见反馈](http://jianyi.baidu.com/)[退出](https://passport.baidu.com/?logout&u=https%3A%2F%2Fbaijiahao.baidu.com%2Fs%3Fid%3D1826187428653369347%26wfr%3Dspider%26for%3Dpc)

编辑：编辑部 HNY

【新智元导读】AI智能体领域Type-C来了！Manus及其开源复现诞生，一夜捧红了MCP，工具调用/访问外部数据，一个协议就够了。

上一周，智能体迎来里程碑式的一周。

从Manus及其开源复现，到Opera的浏览器操作AI智能体、AI工作伴侣Archer，再到多种个人项目，将Agent推向热议风口。

在处理动辄需要十几甚至几十分钟的复杂任务时，涉及到3个核心能力：

规划

工具使用

记忆

其中，第二趴是让智能体「动起来」的关键，真正与现实世界进行交互。

举个例子，当前最强的开源复现OWL在查找伦敦今日放映的电影时，AI智能体主动调用Chrome搜索工具后，精准返回影院的实时信息。

![](https://pic.rmb.bdstatic.com/bjh/250310/dump/cf087495a7e12a2f143c6bb2a92161cd.gif)

而最火的开源项目OpenMauns，在查找Karpathy个人信息主页信息时，也是基于强大的工具使用能力。

![](https://pic.rmb.bdstatic.com/bjh/250310/dump/9fa0ec07f103ef237ebd16f7919aee8e.gif)

这些案例生动地证明了，工具使用，能让智能体跳出空想局限，进化出会做事的能力。

而作为最强的标准化接口协议，MCP也在一夜间爆红硅谷，无人不知。

![](https://pics4.baidu.com/feed/e850352ac65c1038681093968886171cb17e899a.jpeg@f_auto?token=da45a9a4e49d4fbe2ab70001452dd16b)

![](https://pics2.baidu.com/feed/bba1cd11728b47100a699e77f95947f2fd032369.jpeg@f_auto?token=75f251a6d117e26df3ecd6f8d066171b)

对于圈外的人来说，可能对此有所陌生。而它的本质，就是智能体系统的一种。

**一次搭建，代替1亿次配置**

去11月，Anthropic首次提出「模型上下文协议」，即MCP，赋予了Claude模型超级能力，一次构建，让AI与工作流深度集成。

其主要优势如下：

**开发简化：**一次编写，多次集成，无需为每个新集成重写定制代码

**灵活性：**切换AI模型或工具时，不需要复杂的重新配置

**实时响应：**MCP连接保持活跃状态，支持实时上下文更新和交互

**安全性和合规性：**内置访问控制机制和标准化的安全实践

**可扩展性：**随着AI生态系统的扩展，只需连接新的MCP服务器即可轻松添加新功能

![](https://pics3.baidu.com/feed/5882b2b7d0a20cf41c7c4e174d9ecf39aeaf99b4.jpeg@f_auto?token=37fcbcd9ce55c31d975cba32f7f9564a)

用通俗的话讲，MCP就像是专为AI应用设计的通用接口，类似我们日常使用的USB-C。

正如USB-C简化了不同设备与计算机的连接方式，MCP简化了AI模型与数据、工具和服务之间的交互方式。

通过MCP，AI助手不仅能够「读懂」代码，还能「理解」团队讨论、涉及文档等外部信息，提供更加精准的回答。

![](https://pics4.baidu.com/feed/aa18972bd40735fa4f6701aca5c68bbc0e2408b2.jpeg@f_auto?token=3ce068dc3c1fd11a6a2872b7b93f60ba)

MCP是一种标准化协议，用于连接AI智能体与各种外部工具和数据源

相比之下，在没有MCP之前，AI助手要想与外部工具互动，必须通过编写代码并调用API，这意味着每一种具体的连接都需要提前手动编程，效率低下且耗时费力。

更棘手的是，每个AI助手与每个外部工具之间都需要单独进行配置。如果有1000个AI助手和1000个外部工具，理论上需要编写1000×1000=100万个独立的连接代码，工作量简直是个天文数字。

打个比方：API就像是不同的门，其中每扇门都有自己独特的钥匙和使用规则：

![](https://pics7.baidu.com/feed/d009b3de9c82d15834df9da9bb9d9dd7bd3e42f4.jpeg@f_auto?token=cea344ccc3d7a57e486eb9f48e856bc9)

传统API要求开发人员为每个服务或数据源编写定制化的集成代码

而MCP的出现就像为AI助手和外部系统打造了一套通用的「标准语言」，堪称是智能体生态的一次「标准化革命」。

一旦某个AI助手实现了MCP协议，它就能通过这个协议无缝连接上成千上万的外部工具，无需再为每种连接单独编写代码。

同样，外部工具（比如邮件、天气应用等）也只需搭建一次MCP服务器，之后所有支持MCP的AI助手都可以直接与之交互。

假如有1万个AI助手和1万个外部工具。在MCP模式下，每方只需实现一次协议，总共只需2万次配置。

而按照传统编码方式，每种AI助手与每种外部工具都要单独对接，那将是1万×1万=1亿次配置！

这直接使配置效率提高了不止一个维度。

MCP的灵活性也非常突出，它既可以在云端运行，也可以在本地设备上部署，适应性极强。

可以说，MCP就像为AI助手和外部系统之间架设了一条高速路，取代了过去需要技术人员一桥一桥手工搭建的低效模式。

**什么是MCP？**

正如前文所说，MCP（Model Context Protocol）是一种新的开放协议，目的是为LLM提供标准化的上下文信息传递方式，从而实现AI智能体与外部数据及工具的结合。

![](https://pics3.baidu.com/feed/902397dda144ad343664f207ea3588fb33ad85f9.jpeg@f_auto?token=a07a71c5825528f6e83f90e0d3080bfe)

和传统的API相比，MCP的区别在于：

**单一协议：**MCP作为一种标准化的「通用接口」，集成一个MCP意味着可以访问多个工具和服务，而不仅仅是单一服务。

**动态发现：**MCP允许AI模型动态发现并与可用工具交互，无需预先设定每个集成的固定代码。

**双向通信：**MCP支持持续、实时的双向通信——类似于WebSockets。AI模型既可以获取信息，也可以实时触发操作。

其中，实时双向通信的机制如下：

**拉取数据：**LLM向服务器查询上下文信息。例如，查看你的日历安排。

**触发操作：**LLM指示服务器执行具体操作。例如，重新安排会议、发送电子邮件。

![](https://pics5.baidu.com/feed/bba1cd11728b4710e5c164f6f85947f2fd032340.jpeg@f_auto?token=98b5ebfe972582b0252393633fd7a878)

不过，如果应用场景需要精确、可预测的交互模式，并有严格的限制条件，传统API可能更为适合。

MCP提供了广泛、动态的能力，非常适合需要灵活性和上下文感知的场景，但对于高度受控的、确定性的应用可能不是最佳选择。

在以下情况下推荐使用传统API：

需要精细控制和高度特定、受限的功能场景

追求性能优化而需要紧密耦合的系统

要求最高可预测性和最小上下文自主性的应用

架构

MCP采用简单的客户端-服务器架构模式：

**MCP主机：**需要访问外部数据或工具的应用程序（如Claude Desktop或AI驱动的集成开发环境）

**MCP客户端：**与MCP服务器维持专属的一对一连接

**MCP服务器：**轻量级服务器，通过MCP协议提供特定功能，连接到本地或远程数据源

**本地数据源：**MCP服务器安全访问的文件、数据库或服务

**远程服务：**MCP服务器访问的基于互联网的外部API或服务

将MCP比作一座桥梁可以更清晰地理解：MCP本身不处理复杂逻辑；它只是协调AI模型和各种工具之间的数据和指令流通。

![](https://pics5.baidu.com/feed/6159252dd42a2834eca2bfdb60224de514cebf05.jpeg@f_auto?token=b2a831d2bcf271ce379f7fb0c485950e)

具体来说，服务器就是与API进行交互的东西。它可以在远程服务器上（例如，在云上），或者在你的本地系统上。

它包含了所有系统上需要与之交互进而采取行动的代码，比如发送Slack消息、创建文件等等。

如下图所示，可以通过MCP服务，调用GitHub API在仓库里创建代码文件。

![](https://pics0.baidu.com/feed/f636afc379310a55f39210d58cd2c7a683261087.jpeg@f_auto?token=4aaf8f49f32435efe94a02b76527e825)

MCP客户端负责与服务器进行通信。客户端的一个非常酷的特点是它可以同时与多个服务器进行交互。

所以你可以设置专门的服务器来处理GitHub交互和Slack交互，然后把它们接入同一个客户端。

![](https://pics7.baidu.com/feed/b2de9c82d158ccbf37a110d0234f3831b0354165.jpeg@f_auto?token=3fb5f2bfa1b2d6df6ff16f8d9f88fc55)

最重要的，协议是使一切运作的关键。可以将它视为一种永远不会改变的通用语言，MCP服务器和MCP客户端都能使用。

它就像USB接口一样，用于将MCP客户端连接到MCP服务器。

USB接口让手机连接到笔记本电脑，MCP协议让你可以将第三方API连接到桌面应用程序。

![](https://pics2.baidu.com/feed/dbb44aed2e738bd4697cffde9a1c03d9267ff923.jpeg@f_auto?token=d42bc81b30a1980a3268d3eca872672e)

针对各种类型的MCP客户端，Total TypeScript的作者Matt Pocock还进行了一波对比。

可以看到，Claude Desktop和Continue支持资源、提示、工具，功能很全面。5ire和BeeAI Framework就比较有限，工具支持还可以，但其他方面基本不行。Cline也支持资源和工具，但不支持提示。Cursor和Emacs Mcp主要支持工具，其他功能都不行，适合简单工具操作。

![](https://pics5.baidu.com/feed/3801213fb80e7bec03335c0615b93d3799506b96.jpeg@f_auto?token=dff40c33552b849c20db55ac0c49d948)

应用场景

在实际应用中，MCP客户端（例如，client.py中的Python脚本）会与管理各种特定工具（如Gmail、Slack或日历应用）交互的MCP服务器进行通信。

这种标准化大大降低了复杂度，使开发人员能够快速实现复杂的交互功能。

**1\. 行程规划助手**

使用传统API需要为Google日历、电子邮件、航空公司预订API分别编写代码，每个都需要单独的认证、上下文传递和错误处理逻辑。

使用MCP则容易得多，AI助手能够无缝地检查日历可用时间，预订航班，并发送确认邮件——所有这些都通过MCP服务器完成，无需为每个工具单独开发集成代码。

**2\. 高级IDE（智能代码编辑器）**

使用传统API需要手动将开发环境与文件系统、版本控制、包管理器和文档系统集成在一起。

而使用MCP，开发环境将通过单一MCP协议连接这些服务，实现更丰富的上下文感知能力和更智能的代码建议

**3\. 复杂数据分析**

使用传统API需要手动管理与各个数据库和数据可视化工具的连接。

使用MCP AI分析平台能够通过统一的MCP层自动发现并与多个数据库、可视化工具和模拟系统进行交互。

快速入门

MCP集成流程：

**定义功能：**明确规划MCP服务器将提供哪些功能

**实现MCP层：**遵循标准化的MCP协议规范进行开发

**选择传输方式：**在本地传输（stdio）或远程传输（服务器发送事件/WebSockets）之间选择

**创建资源/工具：**开发或连接MCP将要交互的特定数据源和服务

**设置客户端：**在MCP服务器和客户端之间建立安全稳定的连接通道

**MCP用例爆发**

大模型爆火之后，提示工程师成为新型职业。如今，已经有大佬建议，开发者们赶快去构建商业化MCP服务器吧。

![](https://pics1.baidu.com/feed/377adab44aed2e736991c3d1bd96258486d6fa7e.jpeg@f_auto?token=a06677e111851f16d4128d92bde4d32f)

Total TypeScript的作者Matt Pocock仅用28行代码就开发出了一个MCP服务器。

![](https://pics6.baidu.com/feed/bd315c6034a85edffea9a0d872c38d2cdc54754e.jpeg@f_auto?token=6e75cf4c1f57e504b0441cd2f7225033)

Cursor+MCP梦幻联动，即可迅速构建出客户需求的功能，全程无需人类干预。

对于码农来说，又是效率的一次极致提升。AI不仅能帮你写代码，还能自动完成从需求分析到功能上线的全流程。

客户通过Slack发送功能需求，Cursor自动读取消息、构建功能，并创建Pull Request

前Meta研究员、CopilotKit创始人Atai Barkai刚刚开源了一个Open MCP Client的项目。

![](https://pics1.baidu.com/feed/f3d3572c11dfa9ecfb6a99925847730c908fc112.jpeg@f_auto?token=8d88fee15281668cea9e4d555e241f40)

它可以让任何应用，直接与MCP服务器直接对话，实现更更多智能的功能。

只需从Composio中获取一个URL，开发者即可在自己的应用中集成这个MCP的能力，无需从0开发。

![](https://pics1.baidu.com/feed/7e3e6709c93d70cf2f8b72eac24b550fbba12b0e.jpeg@f_auto?token=db6e70ed73a5c719dcd191c43bc9f635)

项目地址：https://open-mcp-client.vercel.app/

Agno的开发者Ashpreet Bedi打造了一款「通用MCP智能体」UAgl，可以借此轻松连接和管理多个MCP服务器。

![](https://pics1.baidu.com/feed/ac4bd11373f082025771872a706c7fe2aa641b6d.jpeg@f_auto?token=b22788c3d615379991a1451581b8e0dd)

开发者Will Brown开源了MCP Test Client，可以在开发过程中测试MCP服务器时既充当服务器（对Claude而言），又充当客户端（对被测试的服务器而言）。

![](https://pics2.baidu.com/feed/7aec54e736d12f2eff96e7447355516d843568ad.jpeg@f_auto?token=bd85f7cc0c99445a641e68283c2248e6)

相关搜索

[MIT开源协议](https://baidu.com/s?word=MIT%E5%BC%80%E6%BA%90%E5%8D%8F%E8%AE%AE&rsv_dl=feed_landingpage_rs&from=1020853i&rsf=2 "MIT开源协议")[mcfo项目](https://baidu.com/s?word=mcfo%E9%A1%B9%E7%9B%AE&rsv_dl=feed_landingpage_rs&from=1020853i&rsf=2 "mcfo项目")[MIT开源协议的使用风险](https://baidu.com/s?word=MIT%E5%BC%80%E6%BA%90%E5%8D%8F%E8%AE%AE%E7%9A%84%E4%BD%BF%E7%94%A8%E9%A3%8E%E9%99%A9&rsv_dl=feed_landingpage_rs&from=1020853i&rsf=2 "MIT开源协议的使用风险")[mit 协议](https://baidu.com/s?word=mit%20%E5%8D%8F%E8%AE%AE&rsv_dl=feed_landingpage_rs&from=1020853i&rsf=2 "mit 协议")

## 评论 2

发表

##### 风雷逐影

点歪科技树！最终又回到了自己怀抱！

03-13 08:05

广东

举报

回复

赞

##### 宸宸花园d7

作者加油💪，期待更多。

03-10 14:31

贵州

举报

回复

赞

没有更多啦

33万获赞 9.9万粉丝

人工智能垂直媒体。

北京中经智元科技发展有限公司官方账号

## 作者最新文章

[![](https://t10.baidu.com/it/u=2005166771,260944914&fm=30&app=106&f=JPEG?w=312&h=208&s=D58204F79E9B00D848B5E5B003007012)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9933714195486873976%22%7D&n_type=1&p_from=3)

[

### 谷歌神器一句话P图全网震动！PS直接淘汰，模特广告业不存在了？

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9933714195486873976%22%7D&n_type=1&p_from=3)

3小时前80阅读

[![](https://t10.baidu.com/it/u=909194185,260936077&fm=30&app=106&f=JPEG?w=312&h=208&s=A4F371941B1337DA00C75F8B0300F09C)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_10286792401712884731%22%7D&n_type=1&p_from=3)

[

### 2025年99%代码AI生成！OpenAI高管宣告没有退路人类将被全面超越

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_10286792401712884731%22%7D&n_type=1&p_from=3)

5小时前321阅读

[![](https://t10.baidu.com/it/u=2235884745,260919213&fm=30&app=106&f=JPEG?w=312&h=208&s=24D4E03393076D4946D849FE03001032)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9027181010082129086%22%7D&n_type=1&p_from=3)

[

### AI搜索风靡，但高达60%引用出错！付费版甚至更糟

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9027181010082129086%22%7D&n_type=1&p_from=3)

10小时前75阅读

## 相关推荐

[![](https://t10.baidu.com/it/u=909321973,260861442&fm=30&app=106&f=JPEG?w=312&h=208&s=BD1EAD5F13EBD4EE0855B1CF0100F033)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_10503807714730413430%22%7D&n_type=1&p_from=4)

[

### 为 AI 输送“养分”，MCP 服务器可能是AI赛道最佳创业风口

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_10503807714730413430%22%7D&n_type=1&p_from=4)

[![](https://t12.baidu.com/it/u=1039155402,260867416&fm=30&app=106&f=JPEG?w=312&h=208&s=58F2B8F2080302CE143AAD010300709B)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9635672297235712962%22%7D&n_type=1&p_from=4)

[

### 为啥全世界都搞不出第二个DeepSeek？

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9635672297235712962%22%7D&n_type=1&p_from=4)

[1评论](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9635672297235712962%22%7D&n_type=1&p_from=4)

[![](https://t11.baidu.com/it/u=3240292367,260883109&fm=30&app=106&f=JPEG?w=312&h=208&s=BAC1A14C451009C25F6FB1110300D0D9)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_8930591340220396693%22%7D&n_type=1&p_from=4)

[

### 十大前沿AI模型实战指南：普通人如何用它创造财富

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_8930591340220396693%22%7D&n_type=1&p_from=4)

[![](https://t12.baidu.com/it/u=4281241175,260859406&fm=30&app=106&f=JPEG?w=312&h=208&s=1C84D214045079CA081953D4030070B4)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9510317062414861225%22%7D&n_type=1&p_from=4)

[

### 百度真的大方，这两款大模型都免费

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9510317062414861225%22%7D&n_type=1&p_from=4)

[![](https://t12.baidu.com/it/u=1958255019,260863410&fm=30&app=106&f=JPEG?w=312&h=208&s=F34160ACFE2382CE1A372D070300F098)](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9773157378639955169%22%7D&n_type=1&p_from=4)

[

### “AI作弊”助程序员线上面试蒙混过关，谷歌等大厂考虑恢复面对面

](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9773157378639955169%22%7D&n_type=1&p_from=4)

[1评论](https://mbd.baidu.com/newspage/data/landingsuper?context=%7B%22nid%22%3A%22news_9773157378639955169%22%7D&n_type=1&p_from=4)

换一换

- 1[中国军队在台海军演 外交部回应](https://www.baidu.com/s?wd=%E4%B8%AD%E5%9B%BD%E5%86%9B%E9%98%9F%E5%9C%A8%E5%8F%B0%E6%B5%B7%E5%86%9B%E6%BC%94+%E5%A4%96%E4%BA%A4%E9%83%A8%E5%9B%9E%E5%BA%94&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)热
- 2[发改委：不得违法延长工作时间](https://www.baidu.com/s?wd=%E5%8F%91%E6%94%B9%E5%A7%94%EF%BC%9A%E4%B8%8D%E5%BE%97%E8%BF%9D%E6%B3%95%E5%BB%B6%E9%95%BF%E5%B7%A5%E4%BD%9C%E6%97%B6%E9%97%B4&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)热
- 3[1-2月份国民经济发展态势向新向好](https://www.baidu.com/s?wd=1-2%E6%9C%88%E4%BB%BD%E5%9B%BD%E6%B0%91%E7%BB%8F%E6%B5%8E%E5%8F%91%E5%B1%95%E6%80%81%E5%8A%BF%E5%90%91%E6%96%B0%E5%90%91%E5%A5%BD&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)
- 4[俄宇航员戴外星面具迎滞留美宇航员](https://www.baidu.com/s?wd=%E4%BF%84%E5%AE%87%E8%88%AA%E5%91%98%E6%88%B4%E5%A4%96%E6%98%9F%E9%9D%A2%E5%85%B7%E8%BF%8E%E6%BB%9E%E7%95%99%E7%BE%8E%E5%AE%87%E8%88%AA%E5%91%98&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)
- 5[阿里1688平台全面取消“仅退款”](https://www.baidu.com/s?wd=%E9%98%BF%E9%87%8C1688%E5%B9%B3%E5%8F%B0%E5%85%A8%E9%9D%A2%E5%8F%96%E6%B6%88%E2%80%9C%E4%BB%85%E9%80%80%E6%AC%BE%E2%80%9D&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)
- 6[3名网红街头拍低俗视频被处罚](https://www.baidu.com/s?wd=3%E5%90%8D%E7%BD%91%E7%BA%A2%E8%A1%97%E5%A4%B4%E6%8B%8D%E4%BD%8E%E4%BF%97%E8%A7%86%E9%A2%91%E8%A2%AB%E5%A4%84%E7%BD%9A&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)
- 7[王晶重提35年前刘嘉玲被绑架内幕](https://www.baidu.com/s?wd=%E7%8E%8B%E6%99%B6%E9%87%8D%E6%8F%9035%E5%B9%B4%E5%89%8D%E5%88%98%E5%98%89%E7%8E%B2%E8%A2%AB%E7%BB%91%E6%9E%B6%E5%86%85%E5%B9%95&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)热
- 8[外卖员建议外卖尽量不点炒菜](https://www.baidu.com/s?wd=%E5%A4%96%E5%8D%96%E5%91%98%E5%BB%BA%E8%AE%AE%E5%A4%96%E5%8D%96%E5%B0%BD%E9%87%8F%E4%B8%8D%E7%82%B9%E7%82%92%E8%8F%9C&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)
- 9[小米高管删除“不做卫生巾”博文](https://www.baidu.com/s?wd=%E5%B0%8F%E7%B1%B3%E9%AB%98%E7%AE%A1%E5%88%A0%E9%99%A4%E2%80%9C%E4%B8%8D%E5%81%9A%E5%8D%AB%E7%94%9F%E5%B7%BE%E2%80%9D%E5%8D%9A%E6%96%87&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)
- 10[久未公开露面的刘强东现身香港](https://www.baidu.com/s?wd=%E4%B9%85%E6%9C%AA%E5%85%AC%E5%BC%80%E9%9C%B2%E9%9D%A2%E7%9A%84%E5%88%98%E5%BC%BA%E4%B8%9C%E7%8E%B0%E8%BA%AB%E9%A6%99%E6%B8%AF&sa=fyb_news_feedpc&rsv_dl=fyb_news_feedpc&from=feedpc)

[设为首页](https://www.baidu.com/cache/sethelp/index.html)© Baidu [使用百度前必读](https://www.baidu.com/duty/)[意见反馈](http://jianyi.baidu.com/)京ICP证030173号 

[京公网安备11000002000001号](http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=11000002000001)