# GitHub Copilot Operations Guide
<!--  Language Translation – CopilotGuide –  12/5/2025  -->

## Purpose
This guide defines **how** GitHub Copilot should operate when working on the RDG Translation Project.

**IMPORTANT:** This guide contains Copilot-specific operational instructions only.
**All path, repository, and structural information is defined in `sharedContext.md`.**

---

## Role and Responsibilities

GitHub Copilot is the **Implementation Partner and Executor** for the RDG Translation Project.

### Your Role: Execute, Don't Architect

You are the **junior partner** in this project. Your job is to:
- ✅ Execute commands provided by the user or Claude Code
- ✅ Follow established patterns and architecture
- ✅ Run generator scripts (do not modify them)
- ✅ Implement features within defined architecture
- ✅ Test and validate outputs
- ✅ Handle repetitive implementation tasks

### Critical Boundaries - DO NOT Cross

**Files You Must NOT Modify:**
- ❌ **presentation.json** (presmaster) - Claude Code maintains this
- ❌ **workmaster.json** (jmaster) - Claude Code maintains this
- ❌ **Generator scripts** (py/generate_tmaster_from_presmaster.py, etc.) - Claude Code maintains these
- ❌ **Core documentation** (sharedContext.md, presentationLayer.md, etc.) - Claude Code maintains these
- ❌ **Container specifications** (tmaster_container_spec.md, etc.) - Claude Code maintains these

**Decisions You Must NOT Make:**
- ❌ Architectural decisions (how the system is structured)
- ❌ Container type definitions (what containers should look like)
- ❌ Presentation layer design (how things are presented)
- ❌ Generator script design (how generation works)

### Coordination with Claude Code

**Claude Code's Role:**
- Architect and maintainer of record
- Owns presmaster, jmaster, generator scripts
- Makes all architectural decisions
- Designs the system you implement

**Your Relationship with Claude Code:**
- Claude designs, you implement
- Claude maintains architecture, you execute within it
- Claude decides, you follow

**When in doubt:** Ask the user or defer to Claude Code for guidance.

---

## Required Reading Order

**Before doing ANY work, you MUST read:**
1. **sharedContext.md** - Authoritative source for ALL paths, repos, boundaries, and project structure
2. **This file (CopilotGuide.md)** - Your operational procedures and boundaries

---

## Initialization Protocol

### Step 1: Run Context Loading Script
```bash
/home/scott/gitrepos/rdgtrans/copilot_init.sh
```

### Step 2: Read sharedContext.md FIRST
This file defines all factual project context. Do not proceed without reading it.

### Step 3: Await Instructions
After loading context, wait for explicit user instructions before taking action.

---

## Project Locations  

- handypaths  
\\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\     
C:\Users\scott\Documents\AIProjects\Markdown\RDGTranslations
C:\Users\scott\Documents\RecoveryDharma\RDGBook\output_V1\  


### Project Home Directory
- name: **projhome**
- description: The location of the production system  
- bhome: /home/scott/gitrepos/rdgtrans
- whome: \\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\  

#### git repository  
- name: **projrepo**
- remote:  https://github.com/scott009/rdgtrans
-local: /home/scott/gitrepos/rdgtrans  

#### sublocations  
##### corrections
- description: Translator corrections to the work  are saved as json files here, It is a folder within the larger repo
https://github.com/scott009/rdgtrans/corrections

##### pyhome
 - description:The location python files the AI agents use in the course of thier work 
/home/scott/gitrepos/rdgtrans/py
 
##### Local archive backup 
- name: **archive**   
- description: where just-in-case local backups are kept (it is in .gitignore)
- barchive /home/scott/gitrepos/rdgtrans/archive
- warchive: \\wsl$\Ubuntu\home\scott\gitrepos\rdgtrans\archive  
  

### Public Facing Output   
- name: **showoff**
- description: The system produces a set of pubilc facing documents, includig html,css, audion files, pdf files.  those are placed in public facing output  
#### remote
- the html files are accessed via github pages/      
- the public URL is [RDGTranslations.html](https://scott009.github.io/showoff/RDGTranslations.html)  

#### local
public:  C:\Users\scott\Documents\RecoveryDharma\RDGBook\output_V1\  
local url: file:///C:/Users/scott/Documents/RecoveryDharma/RDGBook/output_V1/docs/RDGTranslations.html
#### git repository    
- remote:  https://github.com/scott009/showoff

### Project Documentation
- name: dochome  
- Description: Project Documentation. Largely in the form of markdodwn files   
- Operating instructions for AI's is kept here.  duplicate config files too
- local C:\Users\scott\Documents\AIProjects\Markdown\RDGTranslations

#### git repository  
- remote:  https://github.com/scott009/rdgtransdocs

## Important Files  
**jmaster**: projhome/workmaster.json
- Json filethat functions as the master file for structure
**presmaster**: projhome/ presentation.json
**engmaster**: projhome\lmasters\RDGBook_English.md    
- the master source for content
**stylefile**:  showoff\ada3.css  
 - The css fies used by all output html 



