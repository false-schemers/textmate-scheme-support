# textmate-scheme-support
Scheme language support (R7RS+/#F) for TextMate-based editors (Sublime, VS Code, ...)

## Colorizer (scheme.tmLanguage) 
Mostly follows R7RS syntax definitions, with some extensions:
- additional definition and syntax keywords from earlier standards and [#F](https://github.com/false-schemers/sharpF "#F - A Minimalistic Scheme System")
- support for `#&` box syntax

Known colorizer problems (most probably cannot be easily fixed):
- colorizer gets confused by datum prefixes such as `` ` ' , ,@ #& `` if the datum that follows is separated by newlines or comments
- definition coloring can be easily fooled by newlines and/or comments in the first two sub-forms
- `#;` comments use relaxed grammar and may be colored incorrectly in some corner cases
- coloring of backquoted expressions is not very robust; it fails if double-nested (e.g.`` `(a `(b ,,c ',,d) e)) `` or if full forms like `(unquote x)` are used. Reasonable forms from real code are colored reasonably well.
- generally, grammar is relaxed in many places, so some syntax errors won't look like errors (e.g. cons dot can be misplaced).

## Color Theme (schemeLight.tmTheme)
Derived from Visual Studio Light theme, with the following modifications:
- more subdued colors
- context-sensitive coloring of character escapes ("in string" vs. |in symbol| vs. standalone)
- `#f` and `#t` colored differently (red/green)
- introduced definitions are shown in **bold**

## Sublime Text 3 Installation
1. Download the `scheme.tmLanguage` and `schemeLight.tmTheme` files from GitHub.
1. In Sublime Text, open the Command Palette (`Ctrl+Shift+P` on Windows/Linux; `⇧⌘P` on OSX) and choose _Browse Packages_.
1. Place the `scheme.tmLanguage` and `schemeLight.tmTheme` files in the `Packages` directory.
1. Update the `color_scheme` setting in your User Preferences to the path of the new theme (i.e. `"Packages/schemeLight.tmTheme"`).

## Screenshots
![](https://raw.githubusercontent.com/false-schemers/textmate-scheme-support/master/images/screenshot1.png)
![](https://raw.githubusercontent.com/false-schemers/textmate-scheme-support/master/images/screenshot2.png)
