# Localization Guide

This Jekyll site supports multiple languages with English (en) as the default language.

## Supported Languages

- **English (en)** - Default
- **German (de)** - Deutsch
- **French (fr)** - Français
- **Spanish (es)** - Español

## How It Works

1. **Language Data Files**: Located in `_data/` directory
   - `en.yml` - English translations
   - `de.yml` - German translations
   - `fr.yml` - French translations
   - `es.yml` - Spanish translations
   - `languages.yml` - Language configuration

2. **Language Switcher**: A dropdown in the header navigation that allows users to switch languages

3. **Language Detection**: The system detects language preference from:
   - URL parameter (`?lang=de`)
   - Browser localStorage
   - Browser language settings
   - Falls back to default (en)

## Adding a New Language

1. Create a new YAML file in `_data/` (e.g., `it.yml` for Italian)
2. Copy the structure from `en.yml` and translate all strings
3. Add the language to `_data/languages.yml`
4. Add the language code to `languages` array in `_config.yml`

## Translating Content

Edit the language files in `_data/` to update translations:

- `app_name` - App name (usually stays the same)
- `app_description` - Main app description
- `features` - Array of feature objects with `title`, `description`, and `fontawesome_icon_name`
- `footer_made_by` - "Made by" text
- `footer_in` - "in" text (for location)
- `press_kit` - "Press Kit" text

## Usage in Templates

Templates automatically use localized strings:

```liquid
{% assign current_lang = page.lang | default: site.default_lang %}
{% assign lang_data = site.data[current_lang] %}
{{ lang_data.app_description }}
```

## Language Switching

Users can switch languages using:
- The language dropdown in the header
- URL parameter: `?lang=de`
- The system remembers the preference in localStorage

