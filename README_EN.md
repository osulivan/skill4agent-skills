# skill4agent-skills

A collection of skills for skill4agent.

## What is skill4agent?

skill4agent is a platform that collects curated skills, designed specifically for Chinese users. We provide Chinese translations of skills and perform script security checks.

[![skill4agent website](https://raw.githubusercontent.com/osulivan/skill4agent-cli/main/assets/skill4agent_en.png)](https://www.skill4agent.com)

## What is this repository?

This is the official skill repository for skill4agent. Currently, it includes the `search-install-skill-zh` skill, which provides two ways to search and install skills:
- npx command (requires Node.js)
- API call (no Node.js required)

It supports searching skills in Chinese, making it more user-friendly for Chinese users.

### What pain points does search-install-skill-zh solve?

When Chinese users ask AI to search for skills, AI typically uses Chinese keywords since the conversation is in Chinese. However, most skills are in English, making it hard to find results with Chinese searches. This skill solves this problem:

1. **Chinese search support:** The skill4agent platform provides Chinese translations for English skills, enabling searches using Chinese keywords
2. **Script security checks:** The skill4agent platform performs security checks on scripts within skills and records the specific locations of sensitive code
3. **Security recheck:** This skill guides AI to recheck sensitive code, improving the safety of skill usage

## What are Skills?

In the simplest analogy:

- **Prompt** = You're standing next to an intern, telling them "do it this way"
- **MCP/Tool Call** = Giving an intern an access card and computer account, letting them use external tools
- **Skill** = Handing an intern a thick "Position SOP Manual + Templates + Scripts + Checklists" folder

Skills are essentially "reusable professional capability packages" or "standardized SOP toolkits" for AI. Through standardized file structures, they transform human professional expertise into resources that AI agents can read, allowing general AI agents to quickly "transform" into specialized AI agents without needing to develop customized models repeatedly.

When encountering such tasks in the future, AI will refer to this "manual" on its own, executing according to the steps, style, and specifications written inside, without you needing to hand-hold it every time.

## License

MIT
