# [Cursor](https://www.cursor.com/) 使用

1. ✅[Cursor 0.46 更新介绍](https://www.youtube.com/watch?v=bTaOsYYMHs4)
2. ✅[Cursor 小技巧，你可以使用 / 来调出一个和 context 相关的控制选项](https://x.com/vikingmute/status/1893191257310020074)
3. ✅[全新的 Cursor 编程工作流程](https://x.com/Yangyixxxx/status/1896009611637113044)
4. ✅[嫌弃 Cursor 思维太发散了吗？那么，请记得在 cursor 完成一个功能后，让它写一份文档放在 docs 目录下。日后使用这个功能时，只需要将文档附在相关上下文中。这样，你的 cursor 就能精准执行，非常省心。](https://x.com/beihuo/status/1895647183057412226)
5. ✅[Cursor MCP 终极指南](https://x.com/iguangzhengli/status/1894698067989061983)：[用 Cursor MCP + browsertools 插件来体验一下在 Cursor 中自动获取 Chrome dev tools console log 的能力](https://browsertools.agentdesk.ai/installation)
6. ✅[一个专门收录 MCP Server 的网站](https://smithery.ai/)
7. ✅[最近大家说的热火朝天的 MCP，到底有什么神奇功效？](https://x.com/Yangyixxxx/status/1893494130908557571)
8. ✅[用 Cursor 改善生活质量之：一键生成 Git 提交命令、自动 push](https://x.com/EryouHao/status/1896895313853706390)：通过以下步骤在 Cursor 中直接访问和编辑 keybindings.json：打开命令面板（Windows/Linux: Ctrl+Shift+P，macOS: Cmd+Shift+P）输入 "Preferences: Open Keyboard Shortcuts (JSON)"，这将直接打开 keybindings.json 文件，只需在这个文件中按照以下格式添加并保存：
   ```json
   [
     {
       "command": "runCommands",
       "key": "cmd+g cmd+g",
       "args": {
         "commands": [
           "workbench.action.files.save",
           "git.stageAll",
           "cursor.generateGitCommitMessage",
           "git.commit",
           "git.push",
           "workbench.scm.history.focus"
         ]
       }
     }
   ]
   ```
   以上配置的含义：定义了一个快捷键 cmd+g cmd+g，用于一键执行保存文件、暂存 Git 更改、生成提交消息、提交、推送并查看历史记录的完整开发工作流程。
9. [用 Cursor+Claude 3.7 Sonnet 一段话生成高保真 app 原型图的提示词](https://x.com/AlchainHust/status/1896878623539573023)：

   ```text
    我想开发一个{类似小宇宙的播客 app}，现在需要输出高保真的原型图，请通过以下方式帮我完成所有界面的原型设计，并确保这些原型界面可以直接用于开发：
    1、用户体验分析：先分析这个 App 的主要功能和用户需求，确定核心交互逻辑。
    2、产品界面规划：作为产品经理，定义关键界面，确保信息架构合理。
    3、高保真 UI 设计：作为 UI 设计师，设计贴近真实 iOS/Android 设计规范的界面，使用现代化的 UI 元素，使其具有良好的视觉体验。
    4、HTML 原型实现：使用 HTML + Tailwind CSS（或 Bootstrap）生成所有原型界面，并使用 FontAwesome（或其他开源 UI 组件）让界面更加精美、接近真实的 App 设计。
    拆分代码文件，保持结构清晰：
    5、每个界面应作为独立的 HTML 文件存放，例如 home.html、profile.html、settings.html 等。

    - index.html 作为主入口，不直接写入所有界面的 HTML 代码，而是使用 iframe 的方式嵌入这些 HTML 片段，并将所有页面直接平铺展示在 index 页面中，而不是跳转链接。
    - 真实感增强：
    - 界面尺寸应模拟 iPhone 15 Pro，并让界面圆角化，使其更像真实的手机界面。
    - 使用真实的 UI 图片，而非占位符图片（可从 Unsplash、Pexels、Apple 官方 UI 资源中选择）。
    - 添加顶部状态栏（模拟 iOS 状态栏），并包含 App 导航栏（类似 iOS 底部 Tab Bar）。
        请按照以上要求生成完整的 HTML 代码，并确保其可用于实际开发。
   ```

## 2025.03.08

1. [分享两个 MCP 开源示例](https://x.com/akazwz_/status/1897906346844152151)：(1) [Cloudflare Workers 中使用 Flux 生成配图背景图等](https://github.com/akazwz/workers-mcp-demo)；(2) [Node.js 与 Figma 集成](https://github.com/akazwz/mcp-figma)；

## 2025.03.10

1. [如何在大规模项目中使用 cursor](https://getstream.io/blog/cursor-ai-large-projects/)：

   （1）编辑-测试循环是有效使用 AI 的关键：

   - 让 AI 编写代码和测试
   - 执行测试并修复 AI 发现的错误
   - 只有在 AI 完成这些步骤后，再开始人工审查

   （2）设置流程：

   - 使用 Agent 模式 + Claude 3.7 Sonnet
   - 创建专门的 AI 文档文件夹，教 AI 了解代码库的最佳实践
   - 在设置中启用 "Yolo 模式"，允许 Cursor 无需确认即可运行测试

   （3）项目文件工作流：

   - 创建详细的项目描述文件，指导 AI 完成特定功能
   - 使用 AI 验证项目规范本身
   - 可以让 AI 根据示例生成新的项目描述文件

   （4）其他实用技巧：

   - 使用 Git 作为检查点系统
   - 限制单个 Cursor 窗口中的步骤数量
   - 在 Cursor 设置中添加文档，帮助 AI 理解不常用的包
   - 可以同时使用专业 IDE（如 Goland）进行调试和重构

   （5）不仅仅是代码生成：

   - 代码标准化
   - 复杂重构（可以一次调整数百个文件）
   - 生成文档
   - 解释复杂代码段
   - 作为技术理解的强大搜索引擎

   结论
   通过正确设置 Cursor，开发者可以提高 5-30 倍的工作效率，专注于更困难的问题，而让 AI 生成基础部分。关键是建立生成-测试-运行测试循环，创建项目计划，并适应这种新的工作流程。

## 2025.03.12

1. ✅[好用的 MCP 聚合平台](https://mcp.composio.dev/)
2. ✅[28 行代码实现 MCP 服务，可用于 Cursor, Windsurf, Claude Code, Zed... 等任意 MCP 客户端 👏🏻](https://x.com/shao__meng/status/1898897401995563262)
