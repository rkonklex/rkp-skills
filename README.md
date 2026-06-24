# rkp-skills

Robert Konklewski's Claude Code skills, packaged as a plugin.

## Install

**Own machine (auto-load, no command):** clone this repo to `~/.claude/skills/rkp/`.
The `.claude-plugin/plugin.json` makes it load as `rkp@skills-dir` on the next session —
skills become `/rkp:<name>`. No marketplace, no `/plugin install`.

**Share with others / other distribution:** the bundled `marketplace.json` also lets anyone
add this repo as a marketplace and install it:

```
/plugin marketplace add <repo-url-or-local-path>
/plugin install rkp@rkp-skills
```

## Structure

```
.claude-plugin/plugin.json        # makes the folder a skills-dir plugin (name: rkp)
.claude-plugin/marketplace.json   # lets others add it as a marketplace
skills/<name>/SKILL.md            # one folder per skill (auto-discovered)
```
