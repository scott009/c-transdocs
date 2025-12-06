# Translation Master Container Specification v2.0

**Document Type:** Container Type Definition
**Container ID:** `tmaster`
**Version:** 2.0
**Last Updated:** 2025-12-05
**Reference Implementation:** tmasterThai.html

---

## Purpose

The Translation Master (tmaster) container is a web-based correction form that enables bilingual reviewers to:
- View English source text alongside target language translations
- Edit and correct translations
- Add comments and notes
- Toggle UI language between English and target language
- Submit corrections as JSON

---

## Document Structure

### 1. HTML Header
```html
<!DOCTYPE html>
<html lang="{language_code}">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{Language} Translation Master - Correction Tool</title>
    <link rel="stylesheet" href="ada3.css">
    <style>
        /* Embedded CSS - see CSS section below */
    </style>
</head>
```

### 2. Body Structure

#### 2.1 Page Header
```html
<header>
    <h1 data-pr-id="pr_6">{Tool Title}</h1>
</header>
```
- **Elements:** pr_6
- **Purpose:** Display tool title
- **Language-specific:** Yes (via data-pr-id)

#### 2.2 Reviewer Information Section
```html
<div class="reviewer-section">
    <h2 data-pr-id="pr_7">👤 About You</h2>
    <p data-pr-id="pr_27">{Section description}</p>

    <!-- Required Fields -->
    <div class="editor-info">
        <input type="text" id="editor-name"
               data-pr-id="pr_8"
               data-pr-type="placeholder"
               placeholder="{Name placeholder}"
               required>
        <input type="email" id="editor-email"
               data-pr-id="pr_9"
               data-pr-type="placeholder"
               placeholder="{Email placeholder}"
               required>
    </div>

    <!-- Optional Bio Field -->
    <label for="about-yourself" data-pr-id="pr_28">{Bio label}</label>
    <p class="field-note" data-pr-id="pr_29">{Bio note}</p>
    <textarea id="about-yourself" rows="3"
              data-pr-id="pr_30"
              data-pr-type="placeholder"
              placeholder="{Bio placeholder}"></textarea>

    <!-- Optional Overall Notes Field -->
    <label for="overall-notes" data-pr-id="pr_31">{Overall notes label}</label>
    <p class="field-note" data-pr-id="pr_32">{Overall notes note}</p>
    <textarea id="overall-notes" rows="4"
              data-pr-id="pr_33"
              data-pr-type="placeholder"
              placeholder="{Overall notes placeholder}"></textarea>
</div>
```
- **Elements:** pr_7, pr_27, pr_8, pr_9, pr_28, pr_29, pr_30, pr_31, pr_32, pr_33
- **Purpose:** Collect reviewer information and overall feedback
- **Required fields:** name (pr_8), email (pr_9)
- **Optional fields:** bio (pr_30), overall notes (pr_33)

#### 2.3 Content Form - Chapter Title Blocks
```html
<div class="paragraph-block heading-block" data-id="chapter-{N}" data-chapter="{N}">
    <div class="para-header">
        <span class="chapter-num">📖 CHAPTER {N}</span>
        <span class="modified-badge" data-pr-id="pr_36">MODIFIED</span>
    </div>

    <div class="english-ref">
        <label data-pr-id="pr_2">English Chapter Title:</label>
        <p>{English chapter title}</p>
    </div>

    <div class="thai-edit">
        <label data-pr-id="pr_{lang_title_id}">{Language} Chapter Title (editable):</label>
        <textarea name="chapter-{N}"
                  data-original="{Original translation}"
                  data-chapter="{N}">{Current translation}</textarea>
    </div>

    <div class="comment">
        <label data-pr-id="pr_16">Comment (optional):</label>
        <input type="text" name="chapter-{N}-comment"
               data-pr-id="pr_34"
               data-pr-type="placeholder"
               placeholder="{Chapter comment placeholder}">
    </div>
</div>
```
- **Elements:** pr_2, pr_{lang_title_id}, pr_16, pr_34, pr_36
- **Language-specific IDs:** pr_3 (Thai), pr_17 (Japanese), pr_18 (Korean), pr_19 (Simplified Chinese), pr_20 (Traditional Chinese), pr_21 (Vietnamese)
- **Purpose:** Allow editing of chapter titles
- **Repeating:** Yes (one per chapter)

#### 2.4 Content Form - Paragraph Blocks
```html
<div class="paragraph-block" data-id="p{N}-{M}" data-chapter="{N}">
    <div class="para-header">
        <span class="para-id">p{N}-{M}</span>
        <span class="modified-badge" data-pr-id="pr_36">MODIFIED</span>
    </div>

    <div class="english-ref">
        <label data-pr-id="pr_14">English (reference):</label>
        <p>{English paragraph text}</p>
    </div>

    <div class="thai-edit">
        <label data-pr-id="pr_{lang_edit_id}">{Language} (editable):</label>
        <textarea name="p{N}-{M}"
                  data-original="{Original translation}"
                  data-chapter="{N}">{Current translation}</textarea>
    </div>

    <div class="comment">
        <label data-pr-id="pr_16">Comment (optional):</label>
        <input type="text" name="p{N}-{M}-comment"
               data-pr-id="pr_35"
               data-pr-type="placeholder"
               placeholder="{Paragraph comment placeholder}">
    </div>
</div>
```
- **Elements:** pr_14, pr_{lang_edit_id}, pr_16, pr_35, pr_36
- **Language-specific IDs:** pr_15 (Thai), pr_22 (Japanese), pr_23 (Korean), pr_24 (Simplified Chinese), pr_25 (Traditional Chinese), pr_26 (Vietnamese)
- **Purpose:** Allow editing of paragraph translations
- **Repeating:** Yes (one per paragraph, ~351 total)

#### 2.5 Footer
```html
<footer>
    <div class="footer-buttons">
        <button type="button" id="language-toggle">{Language toggle text}</button>
        <button type="button" id="download-btn" data-pr-id="pr_37">Submit</button>
    </div>
    <div id="stats">
        <span id="total-count">396 items (45 chapters + 351 paragraphs)</span>
        <span id="edited-count">0 edited</span>
    </div>
</footer>
```
- **Elements:** pr_37 (submit button), language toggle button (language-specific, not in presmaster)
- **Purpose:** Submit form and toggle UI language
- **Features:** Sticky positioning, real-time edit counter

---

## CSS Requirements

### External Stylesheet
- `ada3.css` - Base project stylesheet

### Embedded CSS Sections
1. **Layout & Structure**
   - body (max-width: 1200px, centered)
   - header (blue background, white text)
   - footer (sticky, white background, shadow)

2. **Reviewer Section**
   - .reviewer-section (blue background, white text, padding)
   - .reviewer-section h2, p, label, textarea (white text styling)
   - .editor-info (flexbox, gap, input styling)
   - .field-note (italic, explanatory text)

3. **Content Blocks**
   - .paragraph-block (light gray background, border, rounded)
   - .heading-block (light blue background for chapters)
   - .paragraph-block.modified (green border, green background tint)
   - .para-header (flexbox, space-between)
   - .para-id, .chapter-num (badges)
   - .modified-badge (green badge, initially hidden)

4. **Form Elements**
   - .english-ref, .thai-edit (content sections)
   - textarea styling (border, padding, focus states)
   - .comment input styling

5. **Language Toggle Button**
   - #language-toggle (blue button, hover effects)
   - .footer-buttons (flexbox layout)

### Total CSS Lines
~304 lines of embedded CSS

---

## JavaScript Requirements

### Module 1: Language Toggle (lines 10649-10722)
```javascript
// Global variables
let currentLanguage = 'english';
let translations = null;

// Load translations from presentation.json
async function loadTranslations() { ... }

// Toggle between English and target language
function toggleLanguage() { ... }

// Initialize on DOMContentLoaded
```

**Functionality:**
- Fetches presentation.json on page load
- Toggles all elements with data-pr-id between English and target language
- Handles different element types (placeholder, button, label, etc.)
- Updates toggle button text
- Graceful fallback if JSON fails to load

**Language-specific values:**
- `currentLanguage` toggle: 'english' ↔ '{language_code}'
- Button text: '{Native language text}' ↔ 'Show in English'

### Module 2: Modification Tracker (lines 10724-10744)
```javascript
// Track which textareas have been modified
// Add .modified class to parent .paragraph-block
// Update edited count in footer
```

**Functionality:**
- Listens to all textarea input events
- Compares current value to data-original
- Adds/removes .modified class
- Updates real-time counter

### Module 3: Submit Handler (lines 10746-10835)
```javascript
// Validate required fields
// Collect all corrections
// Package as JSON
// Submit via Netlify function OR download
```

**Functionality:**
- Validates name and email fields
- Collects all modified content
- Creates JSON correction file
- Attempts POST to Netlify function
- Falls back to download if POST fails

### External JavaScript
- `submit-handler.js` - Netlify submission handler

---

## Data Attributes

### data-pr-id
**Purpose:** Links UI elements to presentation.json translations
**Usage:** All translatable text elements
**Format:** `data-pr-id="pr_{N}"` where N is 2-37
**Count:** ~2000 attributes per file

### data-pr-type
**Purpose:** Specifies how to handle language toggle for element
**Usage:** Input placeholders, textarea placeholders
**Values:** "placeholder"
**Effect:** Updates element.placeholder instead of element.textContent

### data-original
**Purpose:** Stores original translation for comparison
**Usage:** All editable textareas
**Effect:** Enables modification detection

### data-chapter
**Purpose:** Associates content with chapter number
**Usage:** All content blocks (chapter and paragraph)
**Format:** `data-chapter="{N}"` where N is chapter number

### data-id
**Purpose:** Unique identifier for content block
**Usage:** All paragraph-block divs
**Format:** `data-id="chapter-{N}"` or `data-id="p{N}-{M}"`

---

## Language-Specific Variations

### Per-Language Configuration

| Language | Code | Title Label | Edit Label | Toggle Text (Native) |
|----------|------|-------------|------------|----------------------|
| Thai | th | pr_3 | pr_15 | แสดงเป็นภาษาไทย |
| Japanese | ja | pr_17 | pr_22 | 日本語で表示 |
| Korean | ko | pr_18 | pr_23 | 한국어로 표시 |
| Simplified Chinese | zh-CN | pr_19 | pr_24 | 简体中文显示 |
| Traditional Chinese | zh-TW | pr_20 | pr_25 | 繁體中文顯示 |
| Vietnamese | vi | pr_21 | pr_26 | Hiển thị tiếng Việt |

### Language Mapping
```json
{
    "thai": {
        "code": "th",
        "pr_title": "pr_3",
        "pr_edit": "pr_15",
        "toggle_text": "แสดงเป็นภาษาไทย",
        "master_file": "RDGBook_Thai.md"
    },
    "japanese": {
        "code": "ja",
        "pr_title": "pr_17",
        "pr_edit": "pr_22",
        "toggle_text": "日本語で表示",
        "master_file": "RDGBook_Japanese.md"
    }
    // ... etc
}
```

---

## Generation Requirements

### Inputs
1. **workmaster.json** - Chapter/paragraph structure
2. **RDGBook_English.md** - Source text
3. **RDGBook_{Language}.md** - Target language text
4. **presentation.json** - UI translations and structure
5. **Language configuration** - pr_* IDs, toggle text, codes

### Process
1. Read workmaster.json for chapters and paragraph IDs
2. Extract English text from RDGBook_English.md by paragraph ID
3. Extract target language text from RDGBook_{Language}.md by paragraph ID
4. Match English/target pairs by paragraph ID
5. Generate HTML using tmaster template
6. Insert CSS and JavaScript
7. Apply language-specific pr_* IDs
8. Write output file

### Output
- `tmaster{Language}.html` - Complete standalone HTML file

---

## Validation Requirements

A valid tmaster container must have:
- ✅ All 37 pr_* elements present (except language-specific duplicates)
- ✅ Exactly 45 chapter blocks
- ✅ Exactly 351 paragraph blocks
- ✅ Language toggle functionality working
- ✅ Modification tracking working
- ✅ Submit button functional
- ✅ All data-pr-id attributes present
- ✅ All data-original attributes populated
- ✅ CSS and JavaScript embedded correctly

---

## Version History

### v2.0 (2025-12-05)
- Added language toggle feature
- Added comprehensive reviewer section
- Added data-pr-id attributes throughout
- Integrated with presentation.json
- Added real-time modification tracking

### v1.0 (2025-11-28)
- Initial tmaster design
- Basic form structure
- Download-only submission

---

**End of Specification**
