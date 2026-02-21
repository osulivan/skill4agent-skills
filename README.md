# skill4agent-skills

skill4agent 的技能集合。

## 什么是 skill4agent？

[skill4agent.com](https://www.skill4agent.com) 是一个收集精选技能的平台，专为中文用户设计。我们提供技能的中文翻译，并进行脚本安全检查。

[![skill4agent 网站首页](https://raw.githubusercontent.com/osulivan/skill4agent-cli/main/assets/skill4agent_zh.png)](https://www.skill4agent.com)

## 这个仓库是什么？

这是 skill4agent 的官方技能仓库。目前包含 `search-read-install-skill-zh` 技能，该技能提供npx命令和API调用两种方式进行搜索、查阅和安装skill。

### search-read-install-skill-zh 解决什么痛点？

当中文用户让 AI Agent 搜索技能时，因对话中使用中文，AI 通常也默认使用中文关键词进行搜索，但目前大部分 skills 都是英文，导致无法搜索出结果。某些skill存在脚本代码，可能存在安全隐患。这个技能解决了这些问题：

1. **中文搜索支持：** skill4agent 平台对英文 skill 进行了中文翻译，使其能通过中文关键词进行搜索
2. **脚本安全检查：** skill4agent 平台对 skill 中存在的脚本进行代码安全检查，并记录敏感代码的具体位置
3. **安全复检：** 此技能指导 AI 对敏感代码进行复检，提高 skill 使用的安全性

如果你希望你的AI Agent 能帮你搜索、查阅、筛选、安装和检查脚本安全的技能，那么适合使用此技能。

## 什么是技能？

用最简单的比喻来说：

- **提示词（Prompt）** = 你临时站在旁边教实习生"这件事这么做"
- **工具（MCP/Tool Call）** = 给实习生开门禁卡、电脑账号，让他能使用工具进行指定操作
- **技能（Skill）** = 给实习生一本的《技能手册》，当他执行某个任务，需要查阅相关知识时，直接从这本"技能手册"中查阅相关技能，无需自己搜索

技能本质上是给 AI 使用的"可复用专业能力包"。通过标准化的文件结构，将人类的专业经验转化为智能体可读取的资源，让通用智能体快速"变身"为专业智能体，无需重复开发定制化模型。

以后遇到这类任务，AI 自己就会去翻这本"手册"，按里面写好的步骤、风格、规范去执行，不用你每次重新手把手教。

## 许可证

MIT
