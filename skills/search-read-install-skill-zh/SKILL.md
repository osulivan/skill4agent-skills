---
name: search-read-install-skill-zh
description: Use this skill when you need to search, read, and install skills from the online skill library.
---

## Skill Purpose
Help AI learn to use skill4agent CLI commands or API interfaces to implement a complete workflow of searching skills, reading skill details, and installing skills.

## Three Core Operations

### 1. Search Skills (search)
**Purpose**: Find relevant skills, support Chinese, English, or mixed keywords

#### CLI Command (Recommended)
```bash
# Basic search (JSON format is more suitable for AI parsing)
npx skill4agent search <keyword> -j

# Control the number of returned results
npx skill4agent search <keyword> -j -l <number>
```

#### API Interface
```
https://skill4agent.com/api/search?keyword=<keyword>
```

**Parameter Description**:
- `keyword` (required): Search keyword (supports Chinese, English, mixed Chinese and English)
- `limit` (optional): Number of returned results, default 10, maximum 50

**Important Return Fields**:
- `source`: Skill source repository (e.g., `vercel-labs-agent-skills`)
- `skill_name`: Skill name
- `description`: Skill description
- `tags`: Skill tags
- `totalInstalls`: Number of installations
- `read_skill_url`: Skill detail URL
- `download_zip_url`: Skill download URL
- `translation`: Translation information
- `script`: Script check results

### 2. Read Skills (read)
**Purpose**: View detailed information and complete content of skills

#### CLI Command (Recommended)
```bash
# Read original content
npx skill4agent read <source> <skill_name> -j

# Read translated content
npx skill4agent read <source> <skill_name> --type translated -j
```

#### API Interface
```
https://skill4agent.com/api/skills/info?source=<source>&skill_name=<skill_name>
```

**Parameter Description**:
- `source` (required): Skill source repository
- `skill_name` (required): Skill name
- `type` (optional): Content type (`original`/`translated`), default `original`

**Important Return Fields**:
- `skillId`: Unique skill identifier
- `description`: Complete skill description
- `content`: Detailed skill content
- `translation`: Translation information
- `script`: Script check results

### 3. Install Skills (install)
**Purpose**: Install skills to local projects

#### CLI Command
```bash
# Install original skill
npx skill4agent install <source> <skill_name>

# Install translated skill
npx skill4agent install <source> <skill_name> --type translated
```

#### API Interface
```
https://skill4agent.com/api/download/<skillId>?type=<type>
```

**Parameter Description**:
- `skillId` (required): Unique skill identifier
- `type` (optional): Content type (`original`/`translated`), default `original`

## Script Security Check
For skills containing scripts:
- `has_script`: `true` means the skill contains scripts
- `script_check_result`:
  - `safe`: Script is safe
  - `need attention`: Contains sensitive code
- `script_check_notes`: Specific locations of sensitive code, need to recheck after installation

## Scenario-based Workflows

### Scenario 1: Only understand related skills
- **Action**: Use search command
- **Output**: Summarize search results and wait for user's further instructions

### Scenario 2: Find suitable skills to complete tasks
1. **Search**: Use keywords to search for relevant skills
2. **Filter**: Preliminary filter based on `description`, `tags`, `totalInstalls`
3. **Read**: Use read command to get detailed information about candidate skills
4. **Recommend**: Recommend the most suitable skills to users

### Scenario 3: Search and install skills
1. **Search**: Use keywords to search for relevant skills
2. **Filter**: Filter suitable skills based on search results
3. **Read** (Optional): Further understand skill details
4. **Install**: Use install command to install skills

## Search Optimization Suggestions
When no results are found:
1. **Optimize keywords**: Use more general or concise keywords
2. **Switch language**:
   - English search not found → Try Chinese or mixed keywords
   - Chinese search not found → Try English or mixed keywords
3. **Reduce limits**: Decrease the value of `limit` parameter

## Best Practices
- **JSON Format**: It is recommended to add `-j` parameter to search and read commands for better AI parsing
- **Keyword Selection**: Use specific and relevant keywords to improve search accuracy
- **Script Check**: For skills with `script_check_result` as `need attention`, recheck sensitive code after installation
- **Language Version Selection**: Choose appropriate version based on user's preferred language (check original and translated languages via translation field)
- **Script Security Recheck**: If the skill contains scripts with sensitive code, recheck the sensitive code locations listed in `script_check_notes` along with code context after installation to ensure no risks of malicious programs, accessing user private information, modifying or deleting local files, modifying system configurations, etc.
