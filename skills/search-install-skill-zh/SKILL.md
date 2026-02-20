---
name: search-install-skill-zh
description: 当需要搜索和安装在线技能库中的 skills 时使用此技能。
---

## 两种搜索&安装方式

### 方式 1：使用 npx 命令（需要 Node.js 环境，如无环境则使用方式 2）

```bash
# 搜索技能
npx skill4agent search <关键词> -j

# 安装技能（从搜索结果中获取 source 和 skill_name）
npx skill4agent install <source> <skill_name>
```

**可选参数：**
- `-j`：(推荐使用)以 JSON 格式输出搜索结果，方便解析
- `-l <数量>`：控制返回结果数量，默认 10，最大 50

**示例：**
```bash
# 搜索技能
npx skill4agent search react -j
npx skill4agent search 前端开发 -j -l 15
npx skill4agent search SEO优化 -j -l 5

# 安装技能（使用搜索结果中技能的 source 和 skill_name 安装）
npx skill4agent install anthropics/skills frontend-design
```

**安装位置：**
- 当前目录的 `.agents/skills/<skill_name>`

---

### 方式 2：使用 API

**接口地址：**
```
https://skill4agent.com/api/search?keyword=<关键词>
```

**参数：**
- `keyword`（必填）：搜索关键词
- `limit`（可选）：控制返回结果数量，默认 10，最大 50

**示例：**
```
https://skill4agent.com/api/search?keyword=react
https://skill4agent.com/api/search?keyword=前端开发&limit=15
https://skill4agent.com/api/search?keyword=SEO优化&limit=5
```

**安装方法：**
从返回结果的 `download_zip_url` 中获取skill压缩包下载链接，下载 zip 后解压即可获得技能目录。

---

## 传参keyword说明

- 支持纯中文、纯英文、中英混合关键词
- 避免使用特殊字符或空格

## 返回字段说明（脚本相关）

### has_script
- 类型：`true/false`
- 含义：技能是否包含脚本文件

### script_check_result（仅当 has_script 为 true 时显示）
- 可能值：
  - `safe`：脚本安全
  - `need attention`：需要注意（存在敏感代码）

### script_check_notes（仅当 script_check_result 不为 "safe" 时显示）
- 类型：字符串
- 含义：敏感代码的具体位置，建议安装后进行复检

---

## 工作流程

1. 搜索：使用关键词搜索相关技能（可使用中文、英文或中英混合关键词）
2. 筛选：根据搜索结果的 description、tags、installs 字段选择符合需求的技能
3. 安装：使用 npx 命令安装或下载 zip 解压
4. 脚本安全检查：如技能包含脚本并存在敏感代码，安装后需对script_check_notes中记录的敏感代码位置进行检查

---

## 搜索不出结果时

如果搜索结果为空，建议尝试：
1. **优化关键词**：使用更通用或更精简的关键词
2. **换一种语言**：
   - 英文搜不到 → 尝试中文或中英混合
   - 中文搜不到 → 尝试英文或中英混合
