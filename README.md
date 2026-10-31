Contains 2 Windows mappings, 1 macOS mapping and 1 Linux mapping

1. hd - hebrew dvorak - a mapping for hebrew with dvorak, with proper change of ctrl+key functionality to be like the english dvorak layout
2. hw-hd - hardware hebrew dvorak - a mapping for hebrew with dvorak - again with the proper ctrl+key mappings
3. hwhd.keylayout - the macOS variant of hw-hd (see below)

It emulates the [hebrew-dvorak keyboard](https://heboard.wordpress.com/2012/03/30/%d7%a4%d7%a8%d7%99%d7%a9%d7%aa-%d7%9e%d7%a7%d7%9c%d7%93%d7%aa-dvorak-%d7%a2%d7%91%d7%a8%d7%99%d7%aa/) (not the normal hebrew)

4. hwhd.xkb - the Linux (XKB) variant of hw-hd (see below)

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

### Linux (hwhd.xkb)
An XKB port of `hwhd.klc` for keyboards that already send Dvorak in hardware. See also https://github.com/20lives/hebrew-hw-dvorak, a separate Hebrew layout for hardware Dvorak keyboards (installed system-wide via a root script). Its key mappings were not compared with this file and may differ.

Install (X11):
```sh
mkdir -p ~/.xkb/symbols && cp hwhd.xkb ~/.xkb/symbols/hwhd
setxkbmap -I$HOME/.xkb -print hwhd | xkbcomp -I$HOME/.xkb - $DISPLAY
```
Install (Wayland, libxkbcommon >= 1.9 for the `~/.config/xkb` lookup):
```sh
mkdir -p ~/.config/xkb/symbols && cp hwhd.xkb ~/.config/xkb/symbols/hwhd
# sway:  input type:keyboard xkb_layout hwhd
# GNOME: gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'hwhd')]"
```

| Modifier | Output |
|---|---|
| none | Hebrew letters, same as `hwhd.klc` |
| Shift | Latin capitals / shifted symbols |
| Caps Lock | Latin capitals; niqqud on the number row, `` ` `` and `\` |
| Caps Lock+Shift | Hebrew letters |
| AltGr (Ctrl+Alt on Windows) | `4` ₪, `e` €, `u` װ, `h` ײ, `j` ױ, `-` rafe; `[` LRM, `]` RLM |
| AltGr+Shift | `3` LRM, `4` RLM |

Known limitation: XKB has no Ctrl level, so Ctrl+key shortcuts see Hebrew keysyms. GTK/Qt usually fall back to the Latin keycode, but some apps won't. This file is untested on a real Linux machine (written from Windows); please report problems.
