# skill4agent-skills

skill4agent 的技能集合。

## 什么是 skill4agent？

skill4agent 是一个收集精选技能的平台，专为中文用户设计。我们提供技能的中文翻译，并进行脚本安全检查。

[![skill4agent 网站首页](https://raw.githubusercontent.com/osulivan/skill4agent-cli/main/assets/skill4agent_zh.png)](https://www.skill4agent.com)

## 这个仓库是什么？

这是 skill4agent 的官方技能仓库。目前包含 `search-install-skill-zh` 技能，提供两种搜索和安装技能的方式：
- npx 命令（需要 Node.js）
- API 调用（无需 Node.js）

支持使用中文搜索技能，对中文用户更加友好。

## 什么是技能？

用最简单的比喻来说：

- **提示词（Prompt）** = 你临时站在旁边教实习生"这件事这么做"
- **工具（MCP/Tool Call）** = 给实习生开门禁卡、电脑账号，让他能摸到外部工具
- **技能（Skill）** = 直接发给实习生一本厚厚的《岗位SOP手册 + 模板 + 脚本 + 检查清单》文件夹

技能本质上是给 AI 使用的"可复用专业能力包"或"标准化SOP工具包"。通过标准化的文件结构，将人类的专业经验转化为智能体可读取的资源，让通用智能体快速"变身"为专业智能体，无需重复开发定制化模型。

以后遇到这类任务，AI 自己就会去翻这本"手册"，按里面写好的步骤、风格、规范去执行，不用你每次重新手把手教。

## 许可证

MIT
