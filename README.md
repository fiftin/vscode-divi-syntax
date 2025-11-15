# Divi Shortcodes Syntax Highlighting for VS Code

This repository contains a lightweight Visual Studio Code extension that adds syntax highlighting for Divi Builder shortcodes such as `[et_pb_section]`, `[et_pb_row]`, and the rest of the nested module declarations commonly exported by the WordPress Divi theme.

## Features

- Highlights opening, closing, and self-closing Divi shortcode tags
- Gives visual emphasis to shortcode attributes and values
- Provides matching bracket/quote auto-closing tailored to the shortcode format
- Allows embedding standard HTML inside shortcode content without losing highlighting

## Installation

1. Run `npm install -g @vscode/vsce` if you have not installed the VS Code extension packaging tool yet.
2. From this folder, package the extension:

   ```bash
   vsce package
   ```

3. Install the generated `.vsix` file into VS Code by opening the **Extensions** view and choosing **Install from VSIX...**
4. Open files that contain Divi shortcode markup (you can also save files with the `.divi` or `.etpb` extension) to see the highlighting in action.

## Development

- The extension does not include any runtime TypeScript/JavaScript—it is purely a TextMate grammar plus language configuration.
- Update `syntaxes/divi.tmLanguage.json` to tune highlighting rules.
- Use the VS Code `Developer: Inspect TM Scopes` command to debug tokenization.

## Example

The following Divi snippet now receives custom highlighting:

```
[et_pb_section fb_built="1" module_class="product-detail"]
    [et_pb_row column_structure="1_2,1_2"]
        [et_pb_column type="1_2"]
            [et_pb_wc_title][/et_pb_wc_title]
        [/et_pb_column]
    [/et_pb_row]
[/et_pb_section]
```
