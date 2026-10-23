# sisnet-skills

This repository is dedicated to manage all the possible skills that could interact with Sisnet data and files.

The basic folder structure it's just include `.github/skills/` in your project directory. Each skill is a folder containing a `SKILL.md` and, optionally, scripts, examples, or other resources. Teammates get updates through the usual Git workflow—clone, pull, or merge a PR; they don’t need to install it into their personal profile.
```text
your-repo/
└── .github/
    └── skills/
        └── skill-name-1/
            ├── SKILL.md
            └── examples/
            ...
        └── skill-name-2/
            ├── SKILL.md
            └── examples/
```
For a skill intended to work across multiple AI agents, consider `.agents/skills/` instead; VS Code supports both locations. Check that the other agents your team uses support the same location and features.
