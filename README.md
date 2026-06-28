# OrionTalk

![Version](https://img.shields.io/badge/version-1.4.0-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-34d058?style=flat-square)

一个纯前端的 AI 多 Agent 聊天应用。支持单聊、群聊自由讨论、自动回复 Bot，以及 API 配置导出/导入。

## ✨ 功能特性

| 功能 | 说明 |
|------|------|
| **单聊** | 与单个 AI Agent 进行一对一对话，支持流式输出 |
| **群聊** | 多个 AI Agent 同时参与对话，可开启自由讨论模式 |
| **自由讨论** | 群聊中 Agent 轮流发言，围绕话题持续讨论 |
| **自动回复 Bot** | Bot Agent 监听对话，以用户视角自动发表评论并触发 AI 回应 |
| **多 API 提供商** | 支持 Agens / DeepSeek，可自定义 Base URL 和 API Key |
| **Markdown 渲染** | 支持加粗、斜体、代码块、引用等基础 Markdown 格式 |
| **配置管理** | 导出/导入 Agent 配置和聊天记录为 JSON 文件 |
| **响应式设计** | 桌面端三栏布局 + 移动端汉堡菜单，触控目标优化 |

## 🎮 使用方式

### 安装与运行

本项目无需安装任何依赖，直接使用：

1. 用浏览器打开 `index.html` 文件
2. 或在终端启动一个静态服务器：

```bash
# 使用 Python
python -m http.server 8080

# 使用 Node.js
npx serve .

# 使用 PHP
php -S localhost:8000
```

然后访问 http://localhost:8080（或对应端口）。

### 配置 API

1. 点击左侧边栏 → **API** 标签页
2. 选择提供商（Agens 或 DeepSeek）
3. 填入 API Key，点击 **测试连接** 验证
4. 点击 **保存** 生效

### 创建 Agent

1. 点击左侧边栏 → **Agent** 标签页
2. 点击 **新建 Agent** 按钮
3. 设置名称、头像 Emoji 和 System Prompt
4. Agent 创建后可在对话中选择使用

### 新建对话

1. 点击 **对话** 标签页 → **+ 新建对话**
2. 选择 **单聊**（选一个 Agent）或 **群聊**（选多个 Agent）
3. 开始聊天

### 群聊自由讨论

在群聊页面点击 **自由讨论** 按钮，选中的 Agent 会轮流发言，围绕当前话题持续讨论。再次点击可停止。

### 自动回复

在单聊页面点击 **自动回复** 按钮，Bot Agent 会定期读取对话内容，以用户身份发表简短评论，并触发 AI Agent 继续回复。

## 📐 页面结构

```
┌─────────────┬──────────────────────────┬─────────────┐
│  侧边栏     │     主聊天区域            │             │
│  (可拖拽)   │                          │             │
│ ┌─────────┐ │ ┌──────────────────────┐ │             │
│ │OrionTalk│ │ │ 消息列表             │ │             │
│ ├─────────┤ │ │                      │ │             │
│ │ 对话     │ │ │  ┌─ 用户 ─┐         │ │             │
│ │ Agent   │ │ │  │ AI     │         │ │             │
│ │ API     │ │ │  └────────┘         │ │             │
│ │ 配置     │ │ │                      │ │             │
│ └─────────┘ │ └──────────────────────┘ │             │
│             │ ┌──────────────────────┐ │             │
│ 联系方式     │ │ 输入框 + 发送按钮     │ │             │
│             │ └──────────────────────┘ │             │
└─────────────┴──────────────────────────┴─────────────┘
```

## 🛠 技术细节

- **零依赖** — 纯 HTML + CSS + Vanilla JavaScript，无任何框架或包管理器
- **状态管理** — 内存中的 `state` 对象，包含 agents、api、chats 三个核心属性
- **API 通信** — 使用 Fetch API 调用 OpenAI 兼容的 chat completions 接口，支持 SSE 流式响应
- **Markdown** — 内置简易 Markdown 解析器，支持 `**bold**`、`*italic*`、`` `code` ``、``` ```code block``` ```、`> quote`
- **数据存储** — 无持久化存储，刷新页面后数据丢失；可通过配置管理导出/导入完整备份
- **响应式** — CSS Media Query + JS 动态适配，移动端侧边栏变为抽屉式导航

## 📁 文件结构

```
oriontalk/
└── index.html          # 单文件应用（HTML + CSS + JS）
```

整个应用仅一个 `index.html` 文件，所有样式和逻辑内联其中。

## 🎨 设计规范

- **配色** — 深蓝底色 `#1a1a2e` + 天青强调色 `#4fc3f7`
- **气泡** — 用户蓝色、AI 深紫、Bot 橙色，三种角色一目了然
- **动画** — 消息淡入、打字指示器弹跳、侧边栏平滑展开/收起
- **触控优化** — 移动端最小触控目标 44px，输入框 16px 防止 iOS 自动缩放

## ⚠️ 注意事项

- 数据仅保存在内存中，刷新页面会丢失所有对话和配置
- 务必使用 **导出配置和聊天记录** 功能定期备份
- API Key 存储在内存中，不会发送到第三方（除直接调用 API 外）
- 内置 Markdown 解析器功能有限，不支持表格、数学公式等高级语法

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.

---

<!-- ==================== English ==================== -->

# OrionTalk

![Version](https://img.shields.io/badge/version-1.4.0-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-34d058?style=flat-square)

A pure frontend AI multi-Agent chat application. Supports single chat, group free discussion, auto-reply Bot, and API configuration export/import.

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Single Chat** | One-on-one conversation with a single AI Agent, supports streaming output |
| **Group Chat** | Multiple AI Agents participate simultaneously, with free discussion mode |
| **Free Discussion** | Agents take turns speaking, continuously discussing around a topic |
| **Auto-Reply Bot** | Bot Agent listens to conversations and automatically comments from the user's perspective, triggering AI responses |
| **Multi-Provider API** | Supports Agens / DeepSeek, customizable Base URL and API Key |
| **Markdown Rendering** | Supports bold, italic, code blocks, blockquotes and other basic Markdown |
| **Configuration Management** | Export/import Agent configs and chat history as JSON files |
| **Responsive Design** | Desktop three-column layout + mobile hamburger menu, touch target optimized |

## 🎮 Usage

### Installation & Running

No dependencies to install — just use it directly:

1. Open `index.html` in a browser
2. Or start a static server from the terminal:

```bash
# Using Python
python -m http.server 8080

# Using Node.js
npx serve .

# Using PHP
php -S localhost:8000
```

Visit http://localhost:8080 (or the corresponding port).

### Configure API

1. Click sidebar → **API** tab
2. Select provider (Agens or DeepSeek)
3. Enter API Key, click **Test Connection** to verify
4. Click **Save** to apply

### Create Agent

1. Click sidebar → **Agent** tab
2. Click **New Agent** button
3. Set name, avatar emoji, and System Prompt
4. Selected Agents appear in the chat creation dialog

### New Chat

1. Click **Chat** tab → **+ New Chat**
2. Choose **Single** (one Agent) or **Group** (multiple Agents)
3. Start chatting

### Free Discussion

Click **Free Discussion** on the group chat page. Selected Agents will take turns speaking and continuously discuss the topic. Click again to stop.

### Auto-Reply

Click **Auto-Reply** on the single chat page. The Bot Agent periodically reads the conversation and comments from the user's perspective, triggering the AI Agent to continue responding.

## 📐 Layout

```
┌─────────────┬──────────────────────────┬─────────────┐
│  Sidebar    │     Main Chat Area       │             │
│  (resizable)│                          │             │
│ ┌─────────┐ │ ┌──────────────────────┐ │             │
│ │OrionTalk│ │ │  Message List        │ │             │
│ ├─────────┤ │ │                      │ │             │
│ │ Chat    │ │ │  ┌─ User ─┐         │ │             │
│ │ Agents  │ │ │  │ AI     │         │ │             │
│ │ API     │ │ │  └────────┘         │ │             │
│ │ Config  │ │ │                      │ │             │
│ └─────────┘ │ └──────────────────────┘ │             │
│             │ ┌──────────────────────┐ │             │
│  Contacts   │ │  Input + Send Button  │ │             │
│             │ └──────────────────────┘ │             │
└─────────────┴──────────────────────────┴─────────────┘
```

## 🛠 Technical Details

- **Zero Dependencies** — Pure HTML + CSS + Vanilla JavaScript, no frameworks or package managers
- **State Management** — In-memory `state` object with three core properties: agents, api, chats
- **API Communication** — Fetch API to OpenAI-compatible chat completions endpoint, SSE streaming support
- **Markdown** — Built-in lightweight Markdown parser supporting `**bold**`, `*italic*`, `` `code` `` , ``` ```code blocks``` ```, `> quotes`
- **Data Storage** — No persistence; data is lost on refresh. Full backups via JSON export/import
- **Responsive** — CSS Media Queries + JS adaptation; mobile sidebar becomes a drawer navigation

## 📁 File Structure

```
oriontalk/
└── index.html          # Single-file app (HTML + CSS + JS)
```

A single `index.html` file contains all styles and logic inline.

## 🎨 Design Specs

- **Colors** — Deep navy base `#1a1a2e` + sky blue accent `#4fc3f7`
- **Bubbles** — User blue, AI purple, Bot orange — three roles at a glance
- **Animations** — Message fade-in, typing indicator bounce, smooth sidebar open/close
- **Touch Optimization** — 44px minimum touch target on mobile, 16px input font to prevent iOS zoom

## ⚠️ Notes

- Data is stored in memory only — all chats and configs are lost on page refresh
- Use **Export Config & Chat History** regularly to back up your data
- API Keys are stored in memory and only sent directly to the API provider
- Built-in Markdown parser is lightweight — no support for tables, math formulas, etc.

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.
