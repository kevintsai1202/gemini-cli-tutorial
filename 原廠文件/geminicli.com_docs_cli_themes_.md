---
url: "https://geminicli.com/docs/cli/themes/"
title: "Themes | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/cli/themes/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Themes

Copy as MarkdownCopied!

Gemini CLI supports a variety of themes to customize its color scheme and
appearance. You can change the theme to suit your preferences via the `/theme`
command or `"theme":` configuration setting.

## Available Themes

[Section titled “Available Themes”](https://geminicli.com/docs/cli/themes/#available-themes)

Gemini CLI comes with a selection of pre-defined themes, which you can list
using the `/theme` command within Gemini CLI:

- **Dark Themes:**
  - `ANSI`
  - `Atom One`
  - `Ayu`
  - `Default`
  - `Dracula`
  - `GitHub`
- **Light Themes:**
  - `ANSI Light`
  - `Ayu Light`
  - `Default Light`
  - `GitHub Light`
  - `Google Code`
  - `Xcode`

### Changing Themes

[Section titled “Changing Themes”](https://geminicli.com/docs/cli/themes/#changing-themes)

1. Enter `/theme` into Gemini CLI.
2. A dialog or selection prompt appears, listing the available themes.
3. Using the arrow keys, select a theme. Some interfaces might offer a live
preview or highlight as you select.
4. Confirm your selection to apply the theme.

**Note:** If a theme is defined in your `settings.json` file (either by name or
by a file path), you must remove the `"theme"` setting from the file before you
can change the theme using the `/theme` command.

### Theme Persistence

[Section titled “Theme Persistence”](https://geminicli.com/docs/cli/themes/#theme-persistence)

Selected themes are saved in Gemini CLI’s
[configuration](https://geminicli.com/docs/get-started/configuration) so your preference is
remembered across sessions.

* * *

## Custom Color Themes

[Section titled “Custom Color Themes”](https://geminicli.com/docs/cli/themes/#custom-color-themes)

Gemini CLI allows you to create your own custom color themes by specifying them
in your `settings.json` file. This gives you full control over the color palette
used in the CLI.

### How to Define a Custom Theme

[Section titled “How to Define a Custom Theme”](https://geminicli.com/docs/cli/themes/#how-to-define-a-custom-theme)

Add a `customThemes` block to your user, project, or system `settings.json`
file. Each custom theme is defined as an object with a unique name and a set of
color keys. For example:

```
{

  "ui": {

    "customThemes": {

      "MyCustomTheme": {

        "name": "MyCustomTheme",

        "type": "custom",

        "Background": "#181818",

        ...

      }

    }

  }

}
```

**Color keys:**

- `Background`
- `Foreground`
- `LightBlue`
- `AccentBlue`
- `AccentPurple`
- `AccentCyan`
- `AccentGreen`
- `AccentYellow`
- `AccentRed`
- `Comment`
- `Gray`
- `DiffAdded` (optional, for added lines in diffs)
- `DiffRemoved` (optional, for removed lines in diffs)
- `DiffModified` (optional, for modified lines in diffs)

You can also override individual UI text roles by adding a nested `text` object.
This object supports the keys `primary`, `secondary`, `link`, `accent`, and
`response`. When `text.response` is provided it takes precedence over
`text.primary` for rendering model responses in chat.

**Required Properties:**

- `name` (must match the key in the `customThemes` object and be a string)
- `type` (must be the string `"custom"`)
- `Background`
- `Foreground`
- `LightBlue`
- `AccentBlue`
- `AccentPurple`
- `AccentCyan`
- `AccentGreen`
- `AccentYellow`
- `AccentRed`
- `Comment`
- `Gray`

You can use either hex codes (e.g., `#FF0000`) **or** standard CSS color names
(e.g., `coral`, `teal`, `blue`) for any color value. See
[CSS color names](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#color_keywords)
for a full list of supported names.

You can define multiple custom themes by adding more entries to the
`customThemes` object.

### Loading Themes from a File

[Section titled “Loading Themes from a File”](https://geminicli.com/docs/cli/themes/#loading-themes-from-a-file)

In addition to defining custom themes in `settings.json`, you can also load a
theme directly from a JSON file by specifying the file path in your
`settings.json`. This is useful for sharing themes or keeping them separate from
your main configuration.

To load a theme from a file, set the `theme` property in your `settings.json` to
the path of your theme file:

```
{

  "ui": {

    "theme": "/path/to/your/theme.json"

  }

}
```

The theme file must be a valid JSON file that follows the same structure as a
custom theme defined in `settings.json`.

**Example `my-theme.json`:**

```
{

  "name": "My File Theme",

  "type": "custom",

  "Background": "#282A36",

  "Foreground": "#F8F8F2",

  "LightBlue": "#82AAFF",

  "AccentBlue": "#61AFEF",

  "AccentPurple": "#BD93F9",

  "AccentCyan": "#8BE9FD",

  "AccentGreen": "#50FA7B",

  "AccentYellow": "#F1FA8C",

  "AccentRed": "#FF5555",

  "Comment": "#6272A4",

  "Gray": "#ABB2BF",

  "DiffAdded": "#A6E3A1",

  "DiffRemoved": "#F38BA8",

  "DiffModified": "#89B4FA",

  "GradientColors": ["#4796E4", "#847ACE", "#C3677F"]

}
```

**Security Note:** For your safety, Gemini CLI will only load theme files that
are located within your home directory. If you attempt to load a theme from
outside your home directory, a warning will be displayed and the theme will not
be loaded. This is to prevent loading potentially malicious theme files from
untrusted sources.

### Example Custom Theme

[Section titled “Example Custom Theme”](https://geminicli.com/docs/cli/themes/#example-custom-theme)

![Custom theme example](https://geminicli.com/docs/cli/assets/theme-custom.png)

### Using Your Custom Theme

[Section titled “Using Your Custom Theme”](https://geminicli.com/docs/cli/themes/#using-your-custom-theme)

- Select your custom theme using the `/theme` command in Gemini CLI. Your custom
theme will appear in the theme selection dialog.
- Or, set it as the default by adding `"theme": "MyCustomTheme"` to the `ui`
object in your `settings.json`.
- Custom themes can be set at the user, project, or system level, and follow the
same [configuration precedence](https://geminicli.com/docs/get-started/configuration) as other
settings.

* * *

## Dark Themes

[Section titled “Dark Themes”](https://geminicli.com/docs/cli/themes/#dark-themes)

### ANSI

[Section titled “ANSI”](https://geminicli.com/docs/cli/themes/#ansi)

![ANSI theme](https://geminicli.com/assets/theme-ansi.png)

### Atom OneDark

[Section titled “Atom OneDark”](https://geminicli.com/docs/cli/themes/#atom-onedark)

![Atom One theme](https://geminicli.com/assets/theme-atom-one.png)

### Ayu

[Section titled “Ayu”](https://geminicli.com/docs/cli/themes/#ayu)

![Ayu theme](https://geminicli.com/assets/theme-ayu.png)

### Default

[Section titled “Default”](https://geminicli.com/docs/cli/themes/#default)

![Default theme](https://geminicli.com/assets/theme-default.png)

### Dracula

[Section titled “Dracula”](https://geminicli.com/docs/cli/themes/#dracula)

![Dracula theme](https://geminicli.com/assets/theme-dracula.png)

### GitHub

[Section titled “GitHub”](https://geminicli.com/docs/cli/themes/#github)

![GitHub theme](https://geminicli.com/assets/theme-github.png)

## Light Themes

[Section titled “Light Themes”](https://geminicli.com/docs/cli/themes/#light-themes)

### ANSI Light

[Section titled “ANSI Light”](https://geminicli.com/docs/cli/themes/#ansi-light)

![ANSI Light theme](https://geminicli.com/assets/theme-ansi-light.png)

### Ayu Light

[Section titled “Ayu Light”](https://geminicli.com/docs/cli/themes/#ayu-light)

![Ayu Light theme](https://geminicli.com/assets/theme-ayu-light.png)

### Default Light

[Section titled “Default Light”](https://geminicli.com/docs/cli/themes/#default-light)

![Default Light theme](https://geminicli.com/assets/theme-default-light.png)

### GitHub Light

[Section titled “GitHub Light”](https://geminicli.com/docs/cli/themes/#github-light)

![GitHub Light theme](https://geminicli.com/assets/theme-github-light.png)

### Google Code

[Section titled “Google Code”](https://geminicli.com/docs/cli/themes/#google-code)

![Google Code theme](https://geminicli.com/assets/theme-google-light.png)

### Xcode

[Section titled “Xcode”](https://geminicli.com/docs/cli/themes/#xcode)

![Xcode Light theme](https://geminicli.com/assets/theme-xcode-light.png)

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.