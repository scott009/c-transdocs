<!--
OPSEC HEADER — READ BEFORE USING THIS DOCUMENT

This file (sharedContext.md) is the authoritative and canonical source of
factual project context for the rdgtrans system. All AI agents and all
human contributors MUST treat the information in this file as the single,
non-derivative source of truth for project paths, repositories,
terminology, operational boundaries, and system structure.

THIS FILE DEFINES FACTS ONLY.
It must not be rewritten, reorganized, reinterpreted, or “improved” by any
AI model or agent without explicit human instruction.

AI AGENTS (any model, current or future) MUST NOT:
- invent or infer project paths, components, or rules not stated here
- override or contradict any information in this file
- propagate stale information after this file is updated
- alter the format, structure, order, or meaning of this document
- create or modify related repos unless explicitly instructed

If any other document or instruction conflicts with this one,
**sharedContext.md prevails.**

If this file is updated, all agents must immediately consider the new
version authoritative.

This header must remain intact and unmodified unless the human project
owner explicitly approves a change.
-->

# sharedContext.md (v1)
**Project: rdgtrans — RDG Book Translation System**  
**Purpose: Shared Context for ChatGPT, Claude, Copilot, and Human Contributors**  
**Location: dochome**

## 1. Purpose of This Document
This file defines the authoritative shared context for all AI agents (Claude, GitHub Copilot, ChatGPT) and any human developer.

It describes:
- Project locations
- Directory map
- Git repository structure
- AI-safe operational boundaries
- Data flow
- Output locations

This document does not contain operational instructions.  
It contains factual context, paths, constraints, and project guarantees.

## 2. Project Identity
**Project Name:** rdgtrans  
**Description:**  
The system that generates multilingual translations of the Recovery Dharma book. It processes Markdown, JSON, and Python scripts to create final public-facing HTML, CSS, PDF, audio, and related files.

**Primary Project Goals:**
- Maintain accurate English and translated masters
- Produce public-facing documents via automated pipelines
- Support translators with consistent workflows
- Avoid touching unrelated repositories

## 3. Project Home Directories
### WSL Production Home (projhome)
```
/home/scott/gitrepos/rdgtrans
```

### Windows UNC View
```
\\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\
```

This is the ONLY directory where code changes should occur.

## 4. Git Repository Information
**Repository Name:** rdgtrans  
**Remote URL:**  
```
https://github.com/scott009/rdgtrans
```

**Local Clone:**  
```
/home/scott/gitrepos/rdgtrans
```

**Rules:**
- Work happens on branch `scott`
- Production branch is `main`
- No AI agent may create/delete branches without permission
- No AI agent may commit/push without explicit approval

## 5. Important Sublocations
### Operational Scripts (scripts)
```
/home/scott/gitrepos/rdgtrans/scripts
```

**Purpose:** Shell scripts for initialization, backup, and operational tasks

**Contents:**
- `read_docs.sh` - Claude Code initialization script
- `copilot_init.sh` - GitHub Copilot initialization script
- `backup.sh` - Project backup script
- `README.md` - Script documentation with Copilot permissions

### Python Utilities (pyhome)
```
/home/scott/gitrepos/rdgtrans/py
```

### Translator Corrections (corrections)
```
/home/scott/gitrepos/rdgtrans/corrections
Remote: https://github.com/scott009/rdgtrans/corrections
```

### Local Backup Archive (archive)
```
/home/scott/gitrepos/rdgtrans/archive
\\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\archive
```

## 6. Project Documentation (dochome)
Markdown-based system docs, AI instructions, config notes.

Windows Location:
```
C:\Users\scott\Documents\AIProjects\Markdown\RDGTranslations
```

### Working Files Subdirectory
```
C:\Users\scott\Documents\AIProjects\Markdown\RDGTranslations\workingfiles
```

**Purpose:** Temporary working documents, task completion reports, and analysis files that support current work but are not part of core documentation.

**Contents:** Session logs, task reports, analysis documents, convenience files

**Note:** Tracked in git but not canonical documentation. Files may be archived or deleted when no longer needed.

## 7. Public Output (showoff)
Local output directory:
```
C:\Users\scott\Documents\RecoveryDharma\RDGBook\output_V1\
```

Local URL:
```
file:///C:/Users/scott/Documents/RecoveryDharma/RDGBook/output_V1/docs/RDGTranslations.html
```

Remote GitHub Pages Repo:
```
https://github.com/scott009/showoff
```

AI agents should NOT modify this directory unless explicitly told.

## 8. High-Level Data Flow
1. Masters stored in `lmasters/`
2. Python tooling in `py/` processes them
3. Generated files appear in output directory
4. Public output optionally pushed to showoff repo
5. Corrections stored under `corrections/`

## 9. AI Boundaries

### AI Agent Roles and Responsibilities

**Claude Code (Architect and Maintainer of Record):**
- Maintains presentation.json (presmaster) and workmaster.json (jmaster)
- Makes all architectural decisions
- Designs and maintains generator scripts
- Owns core documentation (sharedContext.md, presentationLayer.md, etc.)
- Owns container specifications (tmaster_container_spec.md, etc.)
- Decides project structure and organization

**GitHub Copilot (Implementation Partner and Executor):**
- Executes tasks within established architecture
- Runs generator scripts (does not modify them)
- Follows patterns defined by Claude Code
- Does NOT modify presmaster, jmaster, or generator scripts
- Does NOT make architectural decisions
- Defers to Claude Code or user for guidance

**Key Principle:** Claude Code designs, Copilot implements.

### Directory Permissions

AI Agents May Work In:
- `/home/scott/gitrepos/rdgtrans`
- `/home/scott/gitrepos/rdgtrans/scripts` (run scripts, not modify)
- `/home/scott/gitrepos/rdgtrans/py`
- `/home/scott/gitrepos/rdgtrans/corrections`
- dochome (docs)

AI Agents MAY NOT Touch Unless Instructed:
- InquiryCircle repo
- Any non-project WSL paths
- Any non-project Windows folders
- output_V1 public directory
- showoff repo

## 10. Core Project Files

### workmaster.json (jmaster)
**Location:** `projhome/workmaster.json`
**Purpose:** Central tracking and metadata file for all translations
**Description:**
- Tracks translation status for every paragraph in every language
- References external language master files in lmasters/
- Contains chapter structure, paragraph IDs, and status codes
- Does NOT contain translation text (only references and metadata)

### presentation.json (presmaster)
**Location:** `projhome/presentation.json`
\\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\presentation.json
**Purpose:** Presentation layer configuration and metadata
**Description:**
- Defines how translations are presented to end users
- Contains UI/UX metadata for web pages and documents
- References translation masters, screen masters, and print masters
- Manages document container definitions (not document content itself)

## 11. Shared Vocabulary
| Term | Meaning |
|------|---------|
| projhome | Root of rdgtrans |
| scripts | Operational shell scripts (initialization, backup) |
| pyhome | Python utilities |
| dochome | Documentation folder |
| workingfiles | Temporary working documents (subdirectory of dochome) |
| showoff | Public output repo |
| corrections | Translator correction files |
| archive | Local backups |
| masters/lmasters | Authoritative multilingual sources |
| output | Files for public release |
| jmaster | workmaster.json (central tracking file) |
| presmaster | presentation.json (presentation config) |

## 12. Goals of Shared Context
- Provide identical grounding for all AI agents  
- Prevent accidental writes  
- Support multi-agent workflows  
- Improve clarity and maintainability  

## Version
sharedContext.md — Version 1.2 (2025-12-06)
- Added scripts directory to Important Sublocations
- Added scripts to Shared Vocabulary
- Updated AI Agent permissions to include scripts directory

Previous: Version 1.1 (2025-12-04)
- Added Core Project Files section (workmaster.json and presentation.json)
- Added jmaster and presmaster to vocabulary table
