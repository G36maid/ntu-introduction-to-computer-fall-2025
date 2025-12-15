# Agent Guidelines

## Commands
- **Test/Lint**: No strict build system. Ensure Markdown validity and functional links manually.
- **Run**: N/A (Documentation only).

## Code/Style Guidelines
- **Format**: GitHub Flavored Markdown (GFM). Use headers, lists, and code blocks consistently.
- **Naming**: Files in `notes/` as `XX-topic.md`. Resources in `notes/resources/`.
- **Links**: Use relative paths. Ensure `README.md` indexes all new notes.
- **Commits**: Use Conventional Commits (e.g., `docs: add chapter 5 notes`).

## Workflow
- **Conversion**: Process `course-materials/` (PDF/PPTX) into `notes/`. Extract text/images/links.
- **Validation**: Verify converted content against source. Document errors/missing info.
- **Structure**: Keep original files in `course-materials/`. Do not duplicate binary assets unnecessarily.
