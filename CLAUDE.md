# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a LaTeX-based resume repository that generates a professional PDF resume. The repository uses a custom resume class (`resume.cls`) to provide specialized formatting and structure.

## Build Commands

### Compile the resume to PDF
```bash
pdflatex resume.tex
```

### Full build with LaTeXmk (recommended)
```bash
latexmk -pdf resume.tex
```

### Clean auxiliary files
```bash
latexmk -c
```

### Clean all generated files including PDF
```bash
latexmk -C
```

## Architecture

### Core Files
- **resume.tex**: Main resume content file containing all personal information, work experience, education, skills, and projects
- **resume.cls**: Custom LaTeX document class that defines the resume's structure and styling
  - Provides custom environments: `rSection`, `rSubsection`, `rsemisection`
  - Handles header formatting with name and contact information via `\name{}` and `\address{}` commands
  - Defines spacing, margins, and visual styling for consistent formatting

### Custom LaTeX Environments

The resume.cls defines three main environments for structuring content:

1. **rSection**: Top-level sections (Education, Experience, Skills, etc.)
2. **rSubsection**: Subsections with 4 parameters: company/organization, dates, title/role, location
   - Used for work experience entries with bullet points
3. **rsemisection**: Simplified subsections with 2 parameters: title, dates
   - Used for education and projects without extensive bullet points

### Document Structure

The resume follows this organization:
1. Header with name and contact information (defined via `\name{}` and `\address{}` macros)
2. Summary section (optional, currently active)
3. Education section
4. Work Experience section (multiple rSubsection entries in reverse chronological order)
5. Projects section (currently commented out)
6. Skills section (formatted as a table)

## Working with This Resume

### Editing Content
- Edit `resume.tex` to update resume content
- Personal information is set at the top via `\name{}` and `\address{}` commands
- Each job/role uses the `rSubsection` environment with company, dates, title, and location
- Bullet points within subsections are automatically formatted

### Modifying Layout/Styling
- Edit `resume.cls` to change visual styling, spacing, or structural elements
- Key spacing variables are defined at the bottom of resume.cls (`\namesize`, `\addressskip`, `\sectionlineskip`, etc.)
- Margins are controlled in resume.tex via the geometry package (currently 0.5in left/right, 0.3in top/bottom)

### Output
- The compiled PDF is `resume.pdf` (also copied to `Joshua_Palamuttam_Resume.pdf`)
- Auxiliary files (.aux, .log, .fls, .fdb_latexmk, .synctex.gz) are generated during compilation
