# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a LaTeX-based resume repository that generates a professional PDF resume. The repository uses a custom resume class (`resume.cls`) to provide specialized formatting and structure.

## Build Commands

### Compile the resume to PDF with Tectonic (recommended)
```bash
tectonic -X compile resume.tex
```

### Full build with LaTeXmk and XeLaTeX
```bash
latexmk -xelatex resume.tex
```

### Copy the final named resume
```bash
cp resume.pdf Joshua_Palamuttam_Resume.pdf
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
- **resume.tex**: Main resume content file containing all personal information, work experience, education, skills, and projects; uses T1-encoded Latin Modern typography with a 10-point body font
- **resume.cls**: Custom LaTeX document class that defines the resume's structure and styling
  - Provides custom environments: `rSection`, `rSubsection`, `rsemisection`
  - Handles header formatting with name and contact information via `\name{}` and `\address{}` commands
  - Defines spacing, margins, and visual styling for consistent formatting

### Custom LaTeX Environments

The resume.cls defines three main environments for structuring content:

1. **rSection**: Top-level sections (Education, Experience, Skills, etc.)
2. **rSubsection**: Subsections with 3 parameters: company/organization, dates, and title/location
   - Used for work experience entries with bullet points
3. **rsemisection**: Simplified subsections with 3 parameters: title, dates, and detail/degree
   - Used for education and projects without extensive bullet points

### Document Structure

The resume follows this organization:
1. Header with name and contact information (defined via `\name{}` and `\address{}` macros)
2. Work Experience section (multiple rSubsection entries in reverse chronological order)
3. Education section
4. Skills section (plain one-column labeled lines for ATS readability)

## Working with This Resume

### Editing Content
- Edit `resume.tex` to update resume content
- Personal information is set at the top via `\name{}` and `\address{}` commands
- Each job/role uses the `rSubsection` environment with company, dates, title, and location
- Bullet points within subsections are automatically formatted

### Modifying Layout/Styling
- Edit `resume.cls` to change visual styling, spacing, or structural elements
- Key spacing variables are defined at the bottom of resume.cls (`\namesize`, `\addressskip`, `\sectionlineskip`, etc.)
- Margins are controlled in resume.tex via the geometry package (currently 0.5in on all sides)

### Output
- The compiled PDF is `resume.pdf` (also copied to `Joshua_Palamuttam_Resume.pdf`)
- Auxiliary files (.aux, .log, .fls, .fdb_latexmk, .synctex.gz) are generated during compilation
