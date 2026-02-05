# Creating Agent Skills

## Folder Structure (Recommended)
```
my-skill/
├── SKILL.md (Required) Instructions and metadata
├── scripts/ (Optional) Executable scripts
├── references/ (Optional) Static documentation
└── assets/ (Optional) Templates and other resources
```

## SKILL.md File
The `SKILL.md` file is the core of your skill, using YAML frontmatter for metadata and Markdown for instructions.

```markdown
---
name: code-reviewer
description: Use this skill to review code...
---
# Code Reviewer
Instructions go here.
```

- **name**: Unique identifier; must match directory name.
- **description**: Tells the agent when to activate the skill.
- **Body**: Structured Markdown defining workflows.
