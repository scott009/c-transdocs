# Recovery Dharma Translation Project Specification

**Version:** 2.0
**Last Updated:** 2025-11-26
**Project:** RDG Translation Pipeline Reorganization

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Directory Structure](#directory-structure)
3. [Core Files](#core-files)
4. [Path References](#path-references)
5. [workmaster.json Structure](#workmasterjson-structure)
6. [Data Flow](#data-flow)
7. [Status Tracking System](#status-tracking-system)
8. [Language Support](#language-support)

---

## Project Overview

The Recovery Dharma Translation Project manages translations of the Recovery Dharma Book (v2.0) into multiple Asian languages. The project uses a centralized tracking system (workmaster.json) that references external language master files.

### Key Principles

- **English master file** is the authoritative source of truth (matches printed book)
- **Language files** contain AI-generated translations stored separately
- **workmaster.json** tracks translation status but does NOT contain translation text
- **Paragraph-level granularity** for tracking translation completion

---

## Directory Structure

```
/home/scott/gitrepos/rdgtrans/
├── workmaster.json           # Central tracking/metadata file
├── lmasters/                 # Language master files (definitive translations)
│   ├── RDGBook_English.md
│   ├── RDGBook_Japanese.md
│   ├── RDGBook_Korean.md
│   ├── RDGBook_SimplifiedChinese.md
│   ├── RDGBook_Thai.md
│   ├── RDGBook_TraditionalChinese.md
│   └── RDGBook_Vietnamese.md
├── archive/                  # Backup and historical versions
│   └── workmaster.json.1
├── RDBookV1.md              # Legacy book version
├── PersStoriesCorrected.md  # Personal stories (corrected)
├── PersonalStories.md       # Personal stories (original)
├── Personalstories.md       # Personal stories (variant)
└── toc.md                   # Table of contents
```

---

## Core Files

### workmaster.json

**Purpose:** Central tracking and metadata file
**Location:** `/home/scott/gitrepos/rdgtrans/workmaster.json`
**Size:** ~227KB

The master coordination file that:
- Tracks translation status for every paragraph in every language
- References external language master files (does not contain translation text)
- Maintains metadata about data sources (local/remote paths)
- Defines status codes and tracking schemes
- Contains chapter structure and paragraph IDs

### Language Master Files (lmasters/)

**Purpose:** Definitive language translation files
**Location:** `/home/scott/gitrepos/rdgtrans/lmasters/`
**Format:** Markdown (.md)

| File | Language | Size | Status |
|------|----------|------|--------|
| RDGBook_English.md | English (source) | 141KB | Complete |
| RDGBook_Thai.md | Thai | 312KB | In Progress |
| RDGBook_Vietnamese.md | Vietnamese | 205KB | In Progress |
| RDGBook_Japanese.md | Japanese | 186KB | In Progress |
| RDGBook_Korean.md | Korean | 172KB | In Progress |
| RDGBook_SimplifiedChinese.md | Simplified Chinese | 125KB | In Progress |
| RDGBook_TraditionalChinese.md | Traditional Chinese | 125KB | In Progress |

---

## Path References

### Local Paths (WSL)

```
Project Home:    /home/scott/gitrepos/rdgtrans
Language Masters: /home/scott/gitrepos/rdgtrans/lmasters
Archive:         /home/scott/gitrepos/rdgtrans/archive
```

### Windows Paths

```
Project Home:    \\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans
Language Masters: \\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\lmasters
Documentation:   C:\Users\scott\Documents\AIProjects\Markdown\RDGTranslations
```

### Planned Git Repositories

| Name | Purpose | Remote | Local |
|------|---------|--------|-------|
| rdgtrans | Translation project | https://github.com/scott009/rdgtrans | /home/scott/gitrepos/rdgtrans |
| contentServer | Content server | https://github.com/scott009/contentServer | (TBD) |

**Note:** Remote git integration pending - not yet configured

---

## workmaster.json Structure

### Metadata Section

```json
{
  "metadata": {
    "title": "Recovery Dharma",
    "edition": "2.0",
    "source_file": "Recovery Dharma 2.0.docx",
    "license": "CC BY-SA 4.0",
    "json_version": "3.1",
    "last_updated": "2025-11-22T09:03:19",
    "status_fields": { ... },
    "status_schemes": { ... },
    "data_sources": { ... }
  }
}
```

### data_sources Structure

Each language has local and remote source references:

```json
"english": {
  "local": {
    "source_type": "local",
    "path": "/home/scott/gitrepos/rdgtrans/lmasters",
    "filename": "RDGBook_English.md",
    "required": true,
    "hash": "sha256:...",
    "last_verified": "2025-11-22T09:03:19"
  },
  "remote": {
    "source_type": "github",
    "uri": "https://raw.githubusercontent.com/scott009/RDGAsianMD/scott/workmasters/RDGBook_English.md",
    "required": true,
    "hash": "sha256:...",
    "last_verified": "2025-11-22T09:03:19"
  }
}
```

**Note:** Remote URIs currently point to legacy repository - will be updated in future phase

### Chapters Structure

```json
"chapters": [
  {
    "type": "chapter",
    "id": "ch_2229b70",
    "chapter_number": 9,
    "slug": "what-is-recovery-dharma",
    "chapter_title": "WHAT IS RECOVERY DHARMA?",
    "english_title": 1,
    "thai_title": 1,
    "japanese_title": 1,
    "vietnamese_title": 1,
    "content": [
      {
        "type": "paragraph",
        "id": "p9-1",
        "thai_text": 1,
        "vietnamese_text": 0,
        "japanese_text": 1,
        "english_text": 1
      }
    ]
  }
]
```

---

## Data Flow

### Translation Pipeline

```
┌─────────────────────────────────────────────────────────────┐
│                    TRANSLATION WORKFLOW                      │
└─────────────────────────────────────────────────────────────┘

1. SOURCE OF TRUTH
   RDGBook_English.md (lmasters/)
   ↓
   English text represents the printed book

2. AI TRANSLATION
   Claude Sonnet generates translations
   ↓
   Translations written to language .md files

3. STATUS TRACKING
   workmaster.json updated with status codes
   ↓
   Paragraph-level tracking (0-4 status codes)

4. HUMAN REVIEW
   Native speakers review translations
   ↓
   Status codes updated manually (suspect → corrected → accepted)

5. FINAL OUTPUT
   Language master files in lmasters/
   Ready for publishing/distribution
```

### File Relationships

```
workmaster.json (METADATA/TRACKING)
    ├── References → lmasters/RDGBook_English.md (SOURCE)
    ├── References → lmasters/RDGBook_Thai.md
    ├── References → lmasters/RDGBook_Japanese.md
    ├── References → lmasters/RDGBook_Vietnamese.md
    ├── References → lmasters/RDGBook_Korean.md
    ├── References → lmasters/RDGBook_SimplifiedChinese.md
    └── References → lmasters/RDGBook_TraditionalChinese.md

Note: workmaster.json does NOT contain translation text,
      only status codes that reference external files
```

---

## Status Tracking System

### Status Schemes

#### content_status (for paragraphs and titles)

| Code | Status | Description |
|------|--------|-------------|
| 0 | empty | No translation exists |
| 1 | exists | Translation has been generated |
| 2 | suspect | Translation flagged for review |
| 3 | corrected | Translation reviewed and corrected |
| 4 | accepted | Translation approved by native speaker |

#### chapter_status (for chapters)

| Code | Status | Description |
|------|--------|-------------|
| 0 | empty | No content |
| 1 | draft | Initial content created |
| 2 | suspect | Chapter needs review |
| 3 | accepted | Chapter approved |

### Status Fields by Language

Each language tracks specific fields:

```json
"status_fields": {
  "english": {
    "fields": ["english_text"],
    "value": "content_status"
  },
  "thai": {
    "fields": ["thai_text", "thai_title"],
    "value": "content_status"
  },
  "japanese": {
    "fields": ["japanese_text", "japanese_title"],
    "value": "content_status"
  }
  // ... etc for other languages
}
```

### Example: Chapter 9 Status

**Chapter:** "What is Recovery Dharma?" (ch_2229b70)

**Titles:** All languages = 1 (exists)

**Paragraph p9-1:**
- english_text: 1 ✓ (exists)
- thai_text: 1 ✓ (exists)
- japanese_text: 1 ✓ (exists)
- vietnamese_text: 0 (empty)
- korean_text: 0 (empty)

This shows Thai and Japanese translations exist for this paragraph, while Vietnamese and Korean are pending.

---

## Language Support

### Supported Languages

| Language | Code | Title Field | Text Field | Status |
|----------|------|-------------|------------|--------|
| English | english | english_title | english_text | Source (Complete) |
| Thai | thai | thai_title | thai_text | In Progress |
| Vietnamese | vietnamese | vietnamese_title | vietnamese_text | In Progress |
| Japanese | japanese | japanese_title | japanese_text | In Progress |
| Korean | korean | korean_title | korean_text | In Progress |
| Simplified Chinese | simplified_chinese | Chinese_Simplified_title | simplified_chinese_text | In Progress |
| Traditional Chinese | traditional_chinese | Chinese_Tradition_title | traditional_chinese_text | In Progress |
| Tibetan | tibetan | tibetan_title | tibetan_text | Planned |

### Field Naming Convention

- **Text fields:** `{language}_text` (e.g., `thai_text`, `japanese_text`)
- **Title fields:** `{language}_title` (e.g., `thai_title`, `japanese_title`)
- **Exception:** Chinese uses `Chinese_Simplified_title` and `Chinese_Tradition_title`

---

## Notes

### Current Phase: Project Reorganization

- ✓ Updated local paths in workmaster.json to new structure
- ✓ Established lmasters/ as definitive language file location
- ⏳ Remote git repository configuration (pending)
- ⏳ Python utility scripts adaptation (pending)
- ⏳ Remote URI updates in data_sources (pending)

### Future Phases

1. **Git Integration:** Configure remote repositories and sync mechanisms
2. **Automation:** Adapt Python scripts for new folder structure
3. **Workflow Tools:** Develop tools for status updates and reviews
4. **Publishing Pipeline:** Create output generation for web/print

---

## Document History

| Date | Version | Changes |
|------|---------|---------|
| 2025-11-26 | 1.0 | Initial project specification document |

---

**End of Document**
