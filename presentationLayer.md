# Presentation Layer

## Description

The **Presentation Layer** defines how translated content is displayed and how users interact with it.

### Separation of Concerns

This project maintains a clear separation between:

- **Content Layer** - The book text itself (English, Thai, Korean, Vietnamese, Japanese, Chinese)
  - Managed in: `lmasters/` language files
  - Tracked in: `workmaster.json` (jmaster)

- **Presentation Layer** - How that content is visually displayed and behaviorally interactive
  - Defined in: `presentation.json` (presmaster)
  - Includes: UI labels, form elements, buttons, navigation, layout structure

### Two Aspects of Presentation

**1. Visual Presentation**
- Layout and structure
- Styling and typography
- Responsive design for different devices

**2. Interactive Behavior**
- Button actions and form submissions
- Navigation and user flows
- Dynamic UI elements

### Critical Distinction

**This layer describes the CONTAINERS that house documents, not the documents themselves.**

For example:
- ✅ Presentation layer: "Submit" button, "Email Address" field label, page headers
- ❌ NOT presentation layer: Chapter 9 text, paragraph content, book titles

### Multilingual UI

The presentation layer itself is multilingual - UI elements are translated into all supported languages so users can interact with the interface in their preferred language.

## Detail

### Implementation Method

**Step 1:** Create `presentation.json` (presmaster) containing:
- UI element structure (sections, blocks, fields)
- Translatable UI strings in all languages
- Element IDs and metadata

**Step 2:** Reference presmaster from workmaster.json:
```json
{
  "pmaster": "presentation.json"
}
```

**Step 3:** UI strings organized by language:
- English UI labels
- Thai UI labels
- Japanese, Korean, Chinese, Vietnamese UI labels  

   
#### DataStructure
##### jmaster modification
```json
{
  "presmaster": "presentation.json"
}
```

**Note:** All presentation paths are defined in **sharedContext.md**.

Use the following vocabulary terms when referencing paths:
- **projhome** - Project root directory
- **showoff** - Public output directory (local and remote)
- **pyhome** - Python utilities directory
- **dochome** - Documentation directory
- **lmasters** - Language master files location

See sharedContext.md for current authoritative path values.

##### pmaster


### References
- **sharedContext.md** - Authoritative source for all paths, repositories, and project structure
- **ClaudeGuide.md** - Claude Code operational guide (formerly opguide.md)
- **projspec.md** - Technical specification of the translation system

### linklist
- This is just a simple list of URLs that show the addresses of the RDG Book translated into different languages
#### Linkpaths
- Use local to build accurate file references
**local**: `{showoff}/docs` (see sharedContext.md §7 for current path)
- Use remote to build accurate URLs
**remote**: See sharedContext.md §7 for showoff remote GitHub Pages URL 
  

#### STYLEFILE
ada3.css

#### ENGLISH LANGUAGE SOURCE
rdgBook2.html

#### TRANSLATION MASTERS
tmasterTraditionalChinese.html
tmasterSimplifiedChinese.html
tmasterJapanese.html
tmasterKorean.html
tmasterThai.html
tmasterVietnamese.html

#### SCREEN MASTERS
rdgTraditionalChinese.html
rdgSimplifiedChinese.html
rdgJapanese.html
rdgKorean.html
rdgThai.html
rdgVietnamese.html

#### PRINT MASTERS
rdgTraditionalChinesePrint.html
rdgSimplifiedChinesePrint.html
rdgJapanesePrint.html
rdgKoreanPrint.html
rdgThaiPrint.html
rdgVietnamesePrint.html

====================================
The Recovery Dharmal Translastion Project 
. What are we writing today?  
##   What kind of Document
I want to create a web page  
It will be a simple html document that functions as the map to the existing content I've already generated. 
It will use my defulat sstyesheet  
I have already created the language files and can will supply valid links   
But I want to focus on text, on the message right now. 

### Structure  
#### ENGLISH LANGUAGE SOURCE
text about the book
<link to the web verion of the book> 
#### TRANSLATION MASTERS
Web forms to aid human translators as the assit us by verifying and correcting the translation
<links to Translation masters in all 6 language>

#### PRINT MASTERS
Web pages that work fine on the screen but are also optimized to be saved as pdf files are pinted 
<links to print masters in all 6 language>
   
### Style Guiduince 
  A public-facing explanation for the RDG community
  A translator onboarding guide
  A pitch to potential partners (temples, volunteers, donors)

### Tone  
Hybrid
Warm and community-oriented
Visionary/strategic

### Audience?
Translators
Asian sanghas and monastics?
Donors?
Colborators

Stages   
  
  
Recovery Dharma is a living community of people supporting one another with honesty, compassion, and a shared wish to reduce suffering.   
  
The goal of this project is to create clear, accurate, and culturally grounded translations that help people feel welcomed and understood in their own language.   

We recognize a simple truth: recovery becomes more accessible when teachings are offered in the languages people use every day.


We would love to see a  close collaboration with  sanghas, monastics, translators, and recovery communities across the globe.  We hope these translations will open new doorways for connection, healing, and shared practice.  
  
our goal is to support printed editions, online materials, and community resources that meet people where they are, in the languages that feel most natural to them.