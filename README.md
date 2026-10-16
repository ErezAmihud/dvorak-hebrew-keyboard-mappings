Contains 2 Windows mappings and 1 macOS mapping

1. hd - hebrew dvorak - a mapping for hebrew with dvorak, with proper change of ctrl+key functionality to be like the english dvorak layout
2. hw-hd - hardware hebrew dvorak - a mapping for hebrew with dvorak - again with the proper ctrl+key mappings
3. hwhd.keylayout - the macOS variant of hw-hd (see below)

It emulates the [hebrew-dvorak keyboard](https://heboard.wordpress.com/2012/03/30/%d7%a4%d7%a8%d7%99%d7%a9%d7%aa-%d7%9e%d7%a7%d7%9c%d7%93%d7%aa-dvorak-%d7%a2%d7%91%d7%a8%d7%99%d7%aa/) (not the normal hebrew)

For linux: https://github.com/20lives/hebrew-hw-dvorak

### Method of creation
Using microsoft keyboard layout creator, I took the regular hebrew keyboard and set it so PK_C is the hebrew letter at the place of c in dvoram (i in qwerty)

### macOS (hwhd.keylayout)
A port of `hwhd.klc` for keyboards that already send Dvorak in hardware.

Install:
1. Copy `hwhd.keylayout` to `~/Library/Keyboard Layouts/` (or `/Library/Keyboard Layouts/` for all users)
2. Log out and back in
3. System Settings -> Keyboard -> Input Sources -> Edit -> + -> "Others" -> "Hebrew Dvorak (hardware)"

| Modifier | Output |
|---|---|
| none | Hebrew letters, same as `hwhd.klc` |
| Shift | Latin capitals / shifted symbols |
| Caps Lock | Latin capitals, niqqud on the number row, `` ` `` and `\` (same as the Windows SGCap mapping) |
| Caps Lock+Shift | Hebrew letters |
| Command | QWERTY Latin letters, so shortcuts (Cmd+C, Cmd+V...) act like the English layout |
| Control | standard control characters (for terminals) |
| Option | the Windows Ctrl+Alt extras: `4` ₪, `e` €, `u` װ, `h` ײ, `j` ױ, `-` rafe; `[` LRM, `]` RLM |
| Option+Shift | `3` LRM, `4` RLM (Windows Ctrl+Shift+3/4) |

Note: if "Use Caps Lock to switch to and from ABC" is on (Keyboard -> Input Sources), Caps Lock switches input sources and the niqqud layer is unreachable.
