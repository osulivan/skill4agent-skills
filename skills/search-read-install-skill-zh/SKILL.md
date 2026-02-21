---
name: search-read-install-skill-zh
description: Use this skill when you need to search, read, and install skills from the online skill library.
---

## Skill Purpose
Use skill4agent platform provided CLI commands or API interfaces to implement a complete workflow of searching skills, reading skill details, and installing skills.

## Three Core Operations

### 1. Search Skills (search)
**Purpose**: Find relevant skills, support Chinese, English, or mixed keywords

#### CLI Command (requires Node.js environment)
```bash
# Basic search (recommended to use -j, returns JSON format)
npx skill4agent search <keyword> -j

# Control the number of returned results (recommended to use -j, returns JSON format)
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
- `skillId`: Skill ID
- `source`: Skill source repository
- `skill_name`: Skill name
- `description`: Skill description
- `tags`: Skill tags
- `totalInstalls`: Number of installations
- `read_skill_url`: Skill detail URL
- `download_zip_url`: Skill download URL
- `translation`: Translation information (original language, whether has translation, translated language)
- `script`: Script check information (whether contains scripts, whether contains sensitive code, specific locations of sensitive code)

### 2. Read Skills (read)
**Purpose**: View detailed information and complete content of skills (SKILL.md)

#### CLI Command (requires Node.js environment)
```bash
# Read original content (recommended to use -j, returns JSON format)
npx skill4agent read <source> <skill_name> -j

# Read translated content (recommended to use -j, returns JSON format)
npx skill4agent read <source> <skill_name> --type translated -j
```

#### API Interface
```
https://skill4agent.com/api/skills/info?source=<source>&skill_name=<skill_name>
```

**Parameter Description**:
- `source` (required): Skill source repository (obtained from search results)
- `skill_name` (required): Skill name (obtained from search results)
- `type` (optional): Content type (`original`/`translated`), default `original`

**Important Return Fields**:
- `skillId`: Skill ID
- `source`: Skill source repository
- `skill_name`: Skill name
- `download_zip_url`: Skill download URL
- `translation`: Translation information (original language, whether has translation, translated language)
- `script`: Script check information (whether contains scripts, whether contains sensitive code, specific locations of sensitive code)
- `content`: Detailed skill content (complete content of SKILL.md)

### 3. Install Skills (install)
**Purpose**: Install skills to local projects

#### CLI Command (requires Node.js environment)
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
- `skillId` (required): Skill ID (obtained from search results or skill detail)
- `type` (optional): Content type (`original`/`translated`), default `original`

#### Installation Instructions
- CLI command: Installs to `.agents/skills/<skill_name>` directory under current directory
- API interface: Download ZIP file and extract to get `<skill_name>` directory
- To install the skill to other paths (e.g., user-specified or application-required paths), move it to the target directory yourself

## Script Security Check
Through the returned `script` field, understand whether the skill contains scripts and whether there is sensitive code.

- `has_script`: `true` means the skill contains scripts
- `script_check_result`:
  - `safe`: Script is safe
  - `need attention`: Contains sensitive code
- `script_check_notes`: Specific locations of sensitive code, need to recheck after installation

Note: For skills that contain scripts and sensitive code, you must obtain user consent before installation. After installation, recheck the sensitive code locations listed in `script_check_notes` along with code context to ensure no risks of malicious programs, accessing user private information, modifying or deleting local files, modifying system configurations, etc.

## Scenario-based Workflows

### Scenario 1: Only understand related skills
- **Action**: Use keywords to search for relevant skills
- **Output**: Summarize search results and wait for user's further instructions

### Scenario 2: Find suitable skills to complete tasks
1. **Search**: Use keywords to search for relevant skills
2. **Filter**: Preliminary filter based on `description`, `tags`, `totalInstalls`
3. **Read**: Use read command to get detailed information about candidate skills, analyze whether the skill meets the task requirements
4. **Recommend**: Recommend the most suitable skills to users (if the skill contains scripts with sensitive code, you must inform the user)

### Scenario 3: Search and install skills
1. **Search**: Use keywords to search for relevant skills
2. **Filter**: Filter suitable skills based on search results
3. **Read** (if needed): Further understand skill details, analyze whether the skill meets the task requirements
4. **Install**: Use install command or download ZIP to install skill (for skills containing scripts with sensitive code, do NOT install by yourself without user consent - you must obtain user consent before installing)
5. **Script Security Recheck**: If the skill contains scripts with sensitive code, recheck the sensitive code locations listed in `script_check_notes` along with code context after installation to ensure no risks of malicious programs, accessing user private information, modifying or deleting local files, modifying system configurations, etc.

## Search Optimization Suggestions
When no results are found:
1. **Optimize keywords**: Use more general or concise keywords
2. **Switch language**:
   - English search not found → Try Chinese or mixed keywords
   - Chinese search not found → Try English or mixed keywords

## Best Practices
- **JSON Format**: Search and read commands should add `-j` parameter to return JSON format for easier parsing
- **Language Version Selection**: Choose appropriate version based on user's preferred language (check original and translated languages via translation field)
