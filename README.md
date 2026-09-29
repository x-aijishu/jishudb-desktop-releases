

# JishuDB

**让资料真正成为人和 AI 都能使用的知识。**  
**A local-first knowledge base for humans and AI agents.**

JishuDB 是一个可以同时服务多个 Agent 的知识库。它持续收纳、更新和管理你的文件、文件夹、网页、飞书知识库和 Outlook 邮件正文，让资料能够跨 Agent、跨会话、跨任务长期复用。

资料只需要整理一次。以后无论使用哪个 Agent、开始什么任务，都不必重新查找和上传；当原始内容发生变化时，JishuDB 可以持续同步，让 Agent 使用更新后的资料继续工作。

通过 MCP，你可以把同一份知识连接给不同的 AI Agent，用于问答、研究、核对和内容生产。JishuDB 负责管理长期资料，Agent 负责完成眼前任务。

[下载桌面版](https://github.com/x-aijishu/jishudb-desktop-releases/releases) · [Agent Skills](https://github.com/x-aijishu/jishudb-skills) · [AIJISHU](https://aijishu.com/)

> 本仓库用于 JishuDB 的产品介绍、下载入口和使用指引，不提供产品源代码。

<p align="center">
  <img src="./assets/JishuDBBanner.png" alt="JishuDB" width="100%">
</p>

## What Can JishuDB Do? / 它能做什么

### 一份知识，服务多个 Agent

不同 Agent 不必各自保存一份资料，也不需要在每次新会话中重新上传文件。JishuDB 作为统一的知识服务，通过 MCP 把同一份资料提供给经过允许的 Agent，在不同任务中反复使用。

### 资料整理一次，长期持续使用

把文件、文件夹、网页、飞书知识库和 Outlook 邮件正文收纳到 JishuDB 后，它会持续管理资料及索引。来源内容发生变化时可以继续同步，让后续会话和任务使用更新后的版本。

### 不同形式的资料都能变成知识

除了常见文档，JishuDB 还可以通过 ASR 处理会议录音和上传音频，通过 VLM 理解图片与扫描版文档，并为收纳的资料生成 AI 摘要，减少人工整理成本。

### 搜得到，也能回到原始资料

JishuDB 结合 BM25 关键词检索、向量检索和 Cross-encoder 重排，既能匹配明确关键词，也能找到表达不同但语义相关的内容。搜索和问答结果会尽量保留来源，方便继续打开原文核对。

### 重要资料放进本地保险柜

保险柜中的文件和索引保存在当前设备，不会上传到云端。摘要和资料问答只使用本机 Ollama，不会把文件发送给云端模型；默认情况下 Agent 也无法访问，只有你逐个允许的 MCP 连接才能搜索和读取其中的资料。

## Try It For / 可以用它做什么

```text
在我的项目资料里找到关于产品定位的所有讨论。

比较几份行业报告对同一市场规模的描述，并列出来源。

从飞书知识库里找出这个功能之前的设计决策。

根据内部资料整理一份带出处的研究摘要。

让不同 Agent 使用同一个项目知识库，分别完成研究、PPT 和网站。

检查这段结论能不能在已有资料中找到证据。

整理这段会议录音，并生成一份可以继续检索的摘要。

识别这些扫描文档，把其中的信息加入知识库。
```

## Supported Content / 支持的资料

- PDF、DOCX、TXT、Markdown 和 CSV
- PNG、JPG 等图片资料
- 扫描版文档
- 会议录音和上传的音频
- 本地文件夹
- Feishu / Lark Wiki 知识库
- 公开微信公众号文章和网页
- Outlook 邮件正文
- 手动创建的笔记与文档

## Key Capabilities / 核心能力

### Knowledge Management / 知识管理

- 创建多个知识库，区分不同项目、团队和资料范围
- 管理文档、笔记、网页和同步来源
- 查看导入、解析和索引状态
- 按条件筛选、排序和查找资料
- 使用本地文件夹作为可持续更新的权威来源
- 持续同步来源变化，让后续任务使用更新后的资料
- 通过 ASR 收纳会议录音和上传音频
- 通过 VLM 理解图片与扫描版文档
- 为资料生成 AI 摘要

### Search and Answers / 搜索与问答

- BM25 关键词检索
- 向量语义检索
- 关键词与向量结合的混合检索
- Cross-encoder 结果重排
- 多知识库联合检索和结果去重
- 保留引用来源和所属知识库
- 管理当前会话与历史会话

### Agent and MCP

- 通过 MCP 将同一个知识库连接给多个 AI Agent
- 让资料跨 Agent、跨会话、跨任务长期复用
- 为不同 Agent 提供统一、持续更新的知识来源
- 为 Agent 提供带来源的知识检索
- 支持服务凭据，方便外部工具安全连接
- 配套 Skills 覆盖安装、连接、检索、验收、研究和内容生产

### Vault / 本地保险柜

- 保险柜文件和索引只保存在当前设备
- 文件不会上传到云端
- 摘要和资料问答只使用本机 Ollama
- 默认不允许 Agent 搜索和读取保险柜资料
- 只有用户逐个允许的 MCP 连接才能访问

## Get JishuDB / 获取 JishuDB

### Desktop

前往 [JishuDB Desktop Releases](https://github.com/x-aijishu/jishudb-desktop-releases/releases) 下载桌面版本和查看更新记录。

### Docker

如果你希望自行部署，可以使用容器运行：

```bash
export JISHUDB_AUTH_TOKEN="$(openssl rand -hex 32)"

docker run -d --name jishudb \
  -p 127.0.0.1:8088:8088 \
  -v jishudb-data:/data \
  -e JISHUDB_AUTH_TOKEN="$JISHUDB_AUTH_TOKEN" \
  ghcr.io/x-aijishu/jishudb:latest
```

然后在浏览器中打开：

```text
http://localhost:8088
```

首次创建管理员时，请只在本机回环地址或可信私有网络中操作，不要把尚未初始化的实例直接暴露到公网。

### Homebrew

```bash
brew install x-aijishu/tap/jishudb
```

Homebrew 安装仅在对应公开版本满足发布条件后可用。

## Connected Sources / 连接资料来源

### Feishu / Lark

连接一个或多个只读 Wiki 根节点后，JishuDB 可以同步其中有权访问的文档。连接信息由服务端保存，App Secret 不会返回浏览器。

### Local Folders

你可以登记本地文件夹并把它作为原始资料来源。JishuDB 根据其中的文件生成检索索引；如果删除来源但选择保留文档，已有内容仍可搜索，但将失去原文件访问和完整重建能力。

### Public Articles

可以导入公开网页和微信公众号文章，把分散在互联网上的参考资料放进自己的知识库中统一检索。

### Outlook

可以收纳 Outlook 邮件正文，将邮件中的项目背景、沟通记录和决策信息用于后续检索。当前不包含邮件附件。

## JishuDB Skills

[JishuDB Skills](https://github.com/x-aijishu/jishudb-skills) 帮助 AI Agent 更稳定地使用 JishuDB，而不是只得到一个接口地址。

这些 Skills 覆盖：

- 安装、连接和 MCP 验收
- 知识库搜索与来源核对
- 行业研究与数据核验
- 报告、PPT 和网站制作
- 公众号和小红书内容工作流
- Plaud 会议记录归档

## Boundaries and Security / 使用边界与安全

- 首次管理员创建应在本机或可信私有网络中完成
- 公开部署前必须配置有效的服务凭据
- 反向代理需要正确保留 Host 和 Forwarding Headers
- 导入权限不代表 JishuDB 可以绕过原始平台的访问控制
- 保险柜默认禁止 Agent 访问，必须由用户逐个允许 MCP 连接
- 保险柜的摘要和资料问答依赖本机 Ollama，不会调用云端模型
- Outlook 当前仅收纳邮件正文，不包含附件
- 安装 Skills 不代表 JishuDB 已经连接，也不代表任务已经完成
- AI 生成的答案仍应通过引用回到原始资料核对

## About AIJISHU

JishuDB 由 [AIJISHU](https://aijishu.com/) 团队打造。我们关注 AI Agent、知识工具、评测系统，以及 AI 与真实设备结合的开发体验。

**AIJISHU builds practical AI tools for agents, knowledge, evaluation, and real-world development.**
