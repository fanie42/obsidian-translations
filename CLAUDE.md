# CLAUDE.md - AI Assistant Guide for Obsidian Translations

This document provides comprehensive guidance for AI assistants working with the Obsidian translations repository.

## Repository Overview

**Purpose**: Community-maintained translation files for the Obsidian note-taking application.

**Repository Type**: Translation/localization project containing JSON translation files for 60+ languages.

**Main Branch**: `master`

## Repository Structure

```
obsidian-translations/
├── .github/
│   └── workflows/
│       └── main.yml              # CI workflow for JSON linting
├── {language-code}.json          # Translation files (62 languages)
├── {language-code}.termbase.md   # Term dictionaries (optional)
├── {language-code}.guidelines.md # Translation guidelines (optional)
├── README.md                     # Main documentation
├── package.json                  # npm configuration
└── .eslintrc.json               # ESLint configuration for JSON
```

### Key Files

- **`en.json`**: The canonical English translation file serving as the template for all other languages
- **Language files**: Named using ISO 639-1 codes (e.g., `ja.json`, `fr.json`, `pt-BR.json`)
- **Termbase files**: Language-specific term dictionaries (e.g., `ja.termbase.md`, `ru.termbase.md`)
- **Guidelines files**: Language-specific translation guidelines (e.g., `fa.guidelines.md`)

## File Naming Conventions

### Translation Files
- Format: `{language-code}.json`
- Use ISO 639-1 language codes: https://www.wikiwand.com/en/List_of_ISO_639-1_codes
- Regional variants use hyphens: `pt-BR.json`, `zh-TW.json`
- All lowercase except for regional codes: `en.json`, `pt-BR.json`

### Documentation Files
- Termbase: `{language-code}.termbase.md` (term dictionaries for consistency)
- Guidelines: `{language-code}.guidelines.md` (language-specific translation rules)

## JSON Translation File Structure

Translation files use nested key-value pairs:

```json
{
  "setting": {
    "options": "Options",
    "plugin": "Plugin"
  },
  "label-welcome": "Welcome, {{name}}!"
}
```

### Key Principles

1. **Keys remain unchanged**: Never modify the JSON keys, only the values
2. **Preserve placeholders**: Keep `{{variable}}` syntax unchanged in translations
3. **Maintain JSON validity**: Ensure proper escaping of quotes, backslashes, and special characters
4. **No trailing commas**: JSON does not allow trailing commas

## Translation Workflow

### For New Languages

1. Copy content from `en.json`
2. Create new file as `{language-code}.json`
3. Translate values (not keys)
4. Submit pull request

### For Updates

1. Fork the repository
2. Sync fork with upstream `obsidianmd:master` to avoid conflicts
3. Edit the language JSON file
4. Run linting: `npm run lint`
5. Submit pull request to `master` branch

### For Missing Phrases

1. Locate the language file from README table
2. Search for the exact English phrase
3. Replace with translated phrase
4. Submit pull request

## Development Commands

```bash
# Install dependencies
npm install

# Run JSON linting
npm run lint
```

## CI/CD Pipeline

**GitHub Actions** (`.github/workflows/main.yml`):
- Triggers on: Push and PR to `master` branch
- Runs: `npm install` → `yarn run lint`
- Purpose: Validates JSON syntax and structure

## Translation Guidelines

### Universal Rules

1. **Do not translate**:
   - JSON keys
   - Variable placeholders like `{{name}}`, `{{count}}`
   - File paths in examples
   - Markdown syntax characters
   - Command syntax

2. **Maintain**:
   - Line breaks and formatting
   - Punctuation style appropriate for the language
   - Consistency with existing translations

3. **Consider**:
   - Cultural context and idioms
   - Technical terminology standards in the target language
   - UI space constraints (keep translations reasonably concise)

### Language-Specific Guidelines

Some languages have additional guidelines documented in `.guidelines.md` files:
- **Persian (fa)**: `fa.guidelines.md` - RTL considerations, terminology preferences
- Check for termbase files (`.termbase.md`) for term translation standards

### Common Translation Patterns

| English Pattern | Notes |
|----------------|-------|
| `Welcome, {{name}}!` | Keep `{{name}}` unchanged, translate surrounding text |
| `folder 1/folder 2` | Example paths - translate "folder" but keep structure |
| Button labels | Often single words - use imperative mood appropriate for target language |
| Settings descriptions | Typically declarative sentences |

## Commit Message Conventions

Based on repository history:

```
Update {language}.json
Update {language}.json for {version}
Update strings for {version}
Merge remote-tracking branch 'upstream/master'
```

### Examples
- `Update ja.json`
- `Update ru.json for 1.4.5`
- `Update strings for 1.4.5`

## Pull Request Guidelines

1. **Title**: Clear description of what was translated
   - "Update Japanese translation for 1.4.5"
   - "Add missing translations to fr.json"
   - "Fix typo in German translation"

2. **Description**: Include:
   - What was changed (new translations, updates, fixes)
   - Any translation choices that needed clarification
   - Reference to related issues if applicable

3. **Review**: PRs are reviewed by language maintainers or core team

## Working with AI Assistants

### When Adding/Updating Translations

1. **Always read before editing**: Read the target language file and `en.json` to understand context
2. **Check for termbases**: Look for `{language}.termbase.md` for terminology standards
3. **Validate JSON**: Run `npm run lint` before committing
4. **Preserve formatting**: Maintain the exact indentation and structure
5. **Keep consistency**: Search the file for similar existing translations

### Common Tasks

#### Task: Translate missing strings
```bash
# 1. Read the language file
# 2. Compare with en.json to find missing translations
# 3. Look for English values (untranslated strings)
# 4. Translate while preserving placeholders
# 5. Run lint to validate
```

#### Task: Update for new version
```bash
# 1. Check the latest update commit for en.json
# 2. Identify new strings added
# 3. Translate new strings in target language
# 4. Maintain consistency with existing translations
```

#### Task: Fix translation errors
```bash
# 1. Locate the key in the JSON file
# 2. Verify context by checking en.json
# 3. Apply correction
# 4. Ensure JSON remains valid
```

### What to Avoid

1. **Do not** use machine translation without review
2. **Do not** modify keys or JSON structure
3. **Do not** add or remove translation keys (they must match en.json)
4. **Do not** translate technical terms without checking termbase
5. **Do not** create commits on master branch directly
6. **Do not** force push to shared branches

## Language Status Reference

Check README.md for current language status:
- ✅ Complete and ready
- 🚧 Work in progress

## Technical Constraints

### JSON Escaping Rules
- Quotes: `"` → `\"`
- Backslash: `\` → `\\`
- Newline: Use `\n`
- Tab: Use `\t`

### Character Encoding
- UTF-8 encoding required
- All Unicode characters supported
- RTL languages supported (Arabic, Hebrew, Persian, etc.)

## Repository Maintenance

### Staying Up-to-Date

The English template (`en.json`) is updated with each Obsidian release. Update commits typically have messages like:
- "Update strings for 1.x.x"

When English strings are updated:
1. New keys are added to all language files with English values
2. Translators update these English placeholders to their language
3. PRs are submitted with updated translations

### Merge Conflict Prevention

1. Fork right before starting translation work
2. Sync with upstream before each translation session
3. Use GitHub's Compare UI to pull latest changes
4. Merge upstream changes into your fork regularly

## Support and Community

- **Issues**: For translation questions or errors
- **Discussions**: For general translation topics
- **Chinese translations**: Maintained separately at https://github.com/obsidianzh/obsidian-translations

## Quick Reference for AI Assistants

### Before Making Changes
- [ ] Read target language file
- [ ] Read en.json for context
- [ ] Check for .termbase.md or .guidelines.md
- [ ] Understand the UI context where strings appear

### When Editing Translations
- [ ] Preserve all JSON keys
- [ ] Keep `{{placeholders}}` unchanged
- [ ] Maintain JSON validity
- [ ] Match existing translation style
- [ ] Verify no trailing commas

### Before Committing
- [ ] Run `npm run lint`
- [ ] Check JSON is valid
- [ ] Review translation consistency
- [ ] Write clear commit message
- [ ] Ensure working on correct branch

### Testing Changes
```bash
# Validate JSON syntax
npm run lint

# Check file structure
cat {language}.json | jq . > /dev/null && echo "Valid JSON"
```

## Example Workflow for AI Assistant

```bash
# 1. Understand the task
# Read the issue or request

# 2. Research
git checkout -b claude/update-translation-{lang}
Read en.json
Read {lang}.json
Read {lang}.termbase.md (if exists)

# 3. Make changes
Edit {lang}.json
# Preserve structure, translate values, keep placeholders

# 4. Validate
npm run lint

# 5. Commit
git add {lang}.json
git commit -m "Update {lang}.json for version X.X.X"

# 6. Push
git push -u origin claude/update-translation-{lang}
```

## Notes for Claude Code Agents

- This is a translation project, not a software development project
- No build process, compilation, or tests
- Primary validation is JSON linting
- Changes are typically single-file edits
- Community-driven with multiple contributors per language
- Obsidian team maintains en.json as the source of truth
- Translation quality relies on human language expertise

---

**Last Updated**: 2026-01-09
**Repository**: https://github.com/obsidianmd/obsidian-translations
