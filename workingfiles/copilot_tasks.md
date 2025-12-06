# Copilot Tasks

This file contains tasks designed for GitHub Copilot to execute.

**Remember:** You are the implementation partner. Execute these tasks but do not modify core files (presmaster, jmaster, generator scripts, or documentation).

---

## Task: Create Local Backup

**Purpose:** Create a compressed tar backup of the entire RDG translation project

**Script Location:** `/home/scott/gitrepos/rdgtrans/scripts/backup.sh`

**How to Execute:**
```bash
/home/scott/gitrepos/rdgtrans/scripts/backup.sh
```

**What it does:**
- Backs up projhome, dochome, and showoff directories
- Creates compressed tar.gz file in archive/
- Names file: `rdgtransbackup_TIMESTAMP.tar.gz`
- Excludes .git directories and build artifacts
- Prints backup size and location when complete

**When to run:**
- On user request
- Before major changes
- As needed for safety

**Notes:**
- Archive directory is already in .gitignore
- Backups are local only (not pushed to git)
- Script uses rsync for efficient copying
- Timestamp format: YYYYMMDD_HHMMSS

---

## Future Tasks

Additional tasks for Copilot will be added here as needed.
