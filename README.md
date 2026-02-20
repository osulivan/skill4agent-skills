# skill4agent-skills

skill4agent 的技能集合。

## 什么是 skill4agent？

[skill4agent.com](https://www.skill4agent.com) 是一个收集精选技能的平台，专为中文用户设计。我们提供技能的中文翻译，并进行脚本安全检查。

[![skill4agent 网站首页](https://raw.githubusercontent.com/osulivan/skill4agent-cli/main/assets/skill4agent_zh.png)](https://www.skill4agent.com)

## 这个仓库是什么？

这是 skill4agent 的官方技能仓库。目前包含 `search-install-skill-zh` 技能，提供两种搜索和安装技能的方式：
- npx 命令（需要 Node.js）
- API 调用（无需 Node.js）

支持使用中文搜索技能，对中文用户更加友好。

### search-install-skill-zh 解决什么痛点？

当中文用户让 AI 搜索技能时，因对话使用的是中文，AI 通常也会使用中文关键词进行搜索，但目前大部分 skills 都是英文，导致用中文搜索不出结果。这个技能则解决了这个问题：

1. **中文搜索支持：** skill4agent 平台对英文 skill 都进行了中文翻译，使其能通过中文关键词进行搜索
2. **脚本安全检查：** skill4agent 平台对 skill 中存在的脚本进行代码安全检查，并记录敏感代码的具体位置
3. **安全复检：** 此技能引导 AI 对敏感代码进行复检，提高 skill 使用的安全性

如果你希望你的 Agent 能 **搜索skill → 筛选skill → 安装skill → 检查脚本安全**，全流程自主执行，那么适合使用此技能。

## 什么是技能？

用最简单的比喻来说：

- **提示词（Prompt）** = 你临时站在旁边教实习生"这件事这么做"
- **工具（MCP/Tool Call）** = 给实习生开门禁卡、电脑账号，让他能摸到外部工具
- **技能（Skill）** = 直接发给实习生一本厚厚的《岗位SOP手册 + 模板 + 脚本 + 检查清单》文件夹

技能本质上是给 AI 使用的"可复用专业能力包"或"标准化SOP工具包"。通过标准化的文件结构，将人类的专业经验转化为智能体可读取的资源，让通用智能体快速"变身"为专业智能体，无需重复开发定制化模型。

以后遇到这类任务，AI 自己就会去翻这本"手册"，按里面写好的步骤、风格、规范去执行，不用你每次重新手把手教。

## 许可证

MIT
