# OII for MT Manager

Syntax highlighting for [MT Manager](https://mt2.cn) (MT 管理器). One file, `oii.mtsx`.

Needs MT 2.16.5 or newer.

## Install

1. Copy `oii.mtsx` to your phone.
2. Open it in MT Manager. Confirm the install prompt.
3. Open any `.oii` file. Highlighting is on. You can also pick `OII` by hand from the editor's syntax menu.

## Covers

- `//` and `/* */` comments, `///` doc comments in italic. Comment toggle works.
- `impt`, `fun`, `let`, `if`, `else`, `while`, `for`, `in`, `return`, `desc`
- `true`, `false`, `null`
- node names, attribute keys, quoted keys
- `"strings"` with escapes, `{var}` interpolation, bad escapes and a lone `{` in red
- `"""` multiline strings, only when a newline follows
- raw strings with any number of `#`: `#"..."#`, `##"..."##`, `#"""..."""#`
- ints, hex `0xFF`, oct `0o17`, bin `0b1010`, floats, `1_000`, `#inf` `#-inf` `#nan`
- bare words stay plain. `127.0.0.1` and `2021-02-03` are not numbers, so they are not painted as numbers
- `(type)` annotations
- arrays after `:` or `=`. Words inside are values, not node names
- slashdash `/-`. The marker is red and the parked node, attribute or arg is dimmed like a comment
- func heads with params, lambdas, builtin calls, operators inside func bodies
- `{` `}` and a stray `#` in red. OII has no braces
- `\` line continuation

Bracket pairs `[]` and `()` are highlighted when the cursor sits on one.

## Notes

- A bare word at the start of a statement is painted as a node name. `foo` then `bar` on the next line is really one node with an arg (see "Things that bite" in the main README). A highlighter cannot see that, so `bar` is painted as a node too.
- Slashdash dims a parked node only if its `[` is on the same line as the name.
- An unclosed `#"` paints the rest of the file as a string, matching the lexer's unclosed raw string error.

## Colors

The file reuses MT's built-in styles (`string`, `number`, `keyword`, `tagName`, `attrName`, ...) so it follows your theme, day and night. Custom styles are `docComment`, `disabled`, `slashdash`, `typeAnn`, `funcName` and `builtin`. Edit the `styles` block at the top of `oii.mtsx` to recolor.
