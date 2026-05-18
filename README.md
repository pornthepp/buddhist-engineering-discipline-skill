# Buddhist Engineering Discipline Skill

This repository contains one Claude Code skill:

```text
buddhist-engineering-discipline
```

The skill defines a compact work discipline for AI agents. It focuses on careful reasoning, evidence-based answers, root-cause debugging, current-state checks, and honest communication.

---

## Project Structure

```text
.claude/
  skills/
    buddhist-engineering-discipline/
      SKILL.md
      reference.md
      debug-checklist.md
      examples.md
```

---

## Files

`SKILL.md` is the main skill file. It contains the short behavior rules that Claude Code should load during normal use.

`reference.md` explains the Buddhist principle mapping behind the skill. It is supporting context, not required for every task.

`debug-checklist.md` provides a deeper checklist for debugging and root-cause analysis.

`examples.md` shows before/after response examples that demonstrate the intended behavior.

---

## Installation

Copy the `.claude` folder from this repository into the root of a Claude Code project.

Example:

```text
your-project/
  .claude/
    skills/
      buddhist-engineering-discipline/
        SKILL.md
        reference.md
        debug-checklist.md
        examples.md
```

After copying, Claude Code can discover and use the `buddhist-engineering-discipline` skill from that project.

---

## Purpose

This project is only for maintaining and distributing the `buddhist-engineering-discipline` skill.

It is not an application, library, framework, or runtime service. It does not include build scripts, package dependencies, or executable source code.
