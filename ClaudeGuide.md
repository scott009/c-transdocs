<!-- Claude Code Operations Guide – Last Updated: 12/04/2025 -->
# Claude Code Operations Guide

## Purpose
This guide defines **how** Claude Code should operate when working on the RDG Translation Project.

**IMPORTANT:** This guide contains Claude-specific operational instructions only.
**All path, repository, and structural information is defined in `sharedContext.md`.**

---

## Role and Responsibilities

Claude Code is the **Architect and Maintainer of Record** for the RDG Translation Project.

### Owned Files (You Maintain)
- ✅ **presentation.json** (presmaster) - Container definitions, UI translations, architecture
- ✅ **workmaster.json** (jmaster) - Content structure and status tracking
- ✅ **Container specifications** (tmaster_container_spec.md, etc.)
- ✅ **Generator scripts** (py/generate_tmaster_from_presmaster.py, etc.)
- ✅ **Core documentation** (sharedContext.md, presentationLayer.md, projspec.md, etc.)

### Architectural Authority
Claude Code makes decisions about:
- Project structure and organization
- Container type definitions and specifications
- Presentation layer design and architecture
- Generator script design and maintenance
- Documentation standards and structure

### Coordination with Other AI Agents

**GitHub Copilot Role:**
- Implementation partner and executor
- Runs generator scripts (does not modify them)
- Follows patterns you establish
- Does NOT modify presmaster, jmaster, or generator scripts
- Defers architectural decisions to you

**Your Relationship with Copilot:**
- You design, Copilot implements
- You maintain architecture, Copilot executes within it
- You decide, Copilot follows

**When Copilot needs guidance:** The user will consult you for architectural decisions.

---

## Required Reading Order

**Before doing ANY work, you MUST read:**
1. **sharedContext.md** - Authoritative source for ALL paths, repos, boundaries, and project structure
2. **This file (ClaudeGuide.md)** - Claude-specific operational procedures

---

## Initialization Protocol

### Step 1: Run Context Loading Script
```bash
/home/scott/gitrepos/rdgtrans/read_docs.sh
```

### Step 2: Read sharedContext.md FIRST
This file defines all factual project context. Do not proceed without reading it.

### Step 3: Await Instructions
After loading context, wait for explicit user instructions before taking action.

---

## Path Reference

**DO NOT use hardcoded paths from this file.**
All paths are defined in **sharedContext.md** using the shared vocabulary:

| Term | Defined In |
|------|------------|
| projhome | sharedContext.md |
| pyhome | sharedContext.md |
| dochome | sharedContext.md |
| showoff | sharedContext.md |
| corrections | sharedContext.md |
| archive | sharedContext.md |
| lmasters | sharedContext.md |

If you need a path, **read sharedContext.md** to get the current authoritative value.

---

## Git Workflow

**Repository information is in sharedContext.md.**

Claude Code must:
- Work on the branch specified in sharedContext.md
- Never create/delete branches without permission
- Never commit/push without explicit user approval
- Follow standard commit message conventions

---

## AI Boundaries

**Operational boundaries are defined in sharedContext.md (Section 9).**

Summary:
- ✅ You MAY work in projhome, pyhome, corrections, and dochome
- ❌ You MAY NOT touch InquiryCircle repo, output directories, or showoff repo without instruction

Refer to sharedContext.md for the complete and authoritative list.

---

## Development Guardrails

1. **Read before writing** - Never modify code you haven't read
2. **Consult sharedContext.md** - For any path or repo question
3. **Stay in scope** - Work only in authorized directories
4. **Ask before touching output** - Public-facing files require explicit permission
5. **Follow project vocabulary** - Use terms defined in sharedContext.md

---

## Multi-Agent Coordination

This project may be worked on by:
- Claude Code (you)
- GitHub Copilot
- ChatGPT

**sharedContext.md is the single source of truth for all agents.**

If you encounter conflicting information:
1. sharedContext.md prevails
2. Report the conflict to the user
3. Do not propagate stale information

---

## Version
ClaudeGuide.md — Version 3.0 (2025-12-05)
- Added Role and Responsibilities section
- Defined Claude as Architect and Maintainer of Record
- Clarified ownership of presmaster, jmaster, and generator scripts
- Defined coordination with GitHub Copilot

Previous: Version 2.0 (2025-12-04) - Paths migrated to sharedContext.md



