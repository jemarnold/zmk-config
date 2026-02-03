# ZMK Cradio Configuration

This repository contains a custom ZMK firmware configuration for the Cradio keyboard with optimized layers and behaviors for programming and navigation.

## Layer Structure

The keymap consists of 5 layers, with conditional layer activation:

### Layer 0: Base (QWERTY)
- Standard QWERTY layout with home row mods
- **Left hand mods**: Win (A), Alt (S), Ctrl+Shift (D), Ctrl (F)
- **Right hand mods**: Ctrl (J), Ctrl+Shift (K), Alt (L), Menu (')
- **Thumbs**: Shift (tap/sticky), Backspace (hold for Layer 1), Space (hold for Layer 2), Enter (hold for Layer 3)
- Special punctuation keys with mod-morph behaviors (see below)

### Layer 1: Nav-Sym (Navigation & Symbols)
Activated by holding Backspace key.

**Left side** - Window/tab management:
- Esc/Alt+F4 (double-tap), Ctrl+W, Alt+Tab, Shift+Tab, Ctrl+T
- Tab, Shift+Ctrl+Tab, Ctrl+Tab, Ctrl+Backspace, Delete
- Undo, Cut, Copy, Paste, Redo (Ctrl+Z/X/C/V/Y)

**Right side** - Programming symbols:
- Assignment operators: `<-` (R), ` = ` / ` == ` / ` != ` (tap/double/triple)
- Parentheses (), Ampersand/Percent, At/Caret
- Brackets [], Braces {}, Less-than/LTE, Greater-than/GTE
- Hash/Dollar, Grave, Backslash/Asterisk
- Underscore/Command Palette (Ctrl+Shift+P), Slash/Pipe

### Layer 2: Fn-Num (Function Keys & Numpad)
Activated by holding Space key.

**Left side** - Function keys:
- F1-F10, F11, F12

**Right side** - Number pad with operators:
- Numbers 7-9 (top), 4-6 (middle), 1-3 (bottom), 0 (thumb)
- Operators: +/ ` + ` , */ ` * ` , =/ ` = ` , -/ ` - ` , ./, // ` / ` 
- Single tap for operator, double tap for spaced operator

### Layer 3: Nav-Nav (Extended Navigation)
Activated by holding Enter key.

**Left side** - Window switcher:
- Win+1 through Win+5 (tri-state swapper for quick window switching)

**Right side** - Cursor navigation:
- Arrow keys: Home, Up, End, Page Up
- Arrow keys: Left, Down, Right, Page Down  
- Ctrl+Arrow keys for word/paragraph jumping
- Ctrl+Home, Ctrl+End for document start/end

### Layer 4: Sys (System/Bluetooth/Media)
Conditional layer - automatically activated when both Layer 1 and Layer 2 are held simultaneously.

**Left side** - Bluetooth management:
- BT Select 0-3, BT Clear
- BT Disconnect 0-3
- Soft Off, System Reset, Bootloader, Output toggle (BLE/USB)

**Right side** - Media & system controls:
- Volume Up/Down/Mute
- Media: Previous, Play/Pause, Next
- Brightness Up/Down
- Bootloader, System Reset, Soft Off

## Custom Behaviors

### Hold-Tap Behaviors

#### Home Row Mods
- **htl** (left_hand_hold_tap): 280ms tapping term, activates only when opposite hand is used
- **htr** (right_hand_hold_tap): 280ms tapping term, activates only when opposite hand is used
- Both use 175ms quick-tap and 150ms require-prior-idle for improved typing accuracy

#### Layer Tap
- **lt** (layer_tap): 200ms tapping term, balanced flavor for layer access on hold

### Tri-State Behaviors
Used for persistent modifier states that auto-release:

- **alt_tab**: Alt+Tab window switching (stays active for repeated tabs)
- **win_1** through **win_5**: Win+Number for workspace/window switching

### Tap-Dance Behaviors

- **dt_esc_alt_f4**: Esc (tap) → Alt+F4 (double-tap)
- **dt_equal_ops**: ` = ` (tap) → ` == ` (double) → ` != ` (triple)
- **dt_assign_pipe**: `<-` R assignment (tap) → `|>` pipe (double) 
- **dt_minus_spaced_minus**: `-` (tap) → ` - ` (double)
- **dt_plus_spaced_plus**: `+` (tap) → ` + ` (double)
- **dt_asterisk_spaced_asterisk**: `*` (tap) → ` * ` (double)
- **dt_slash_spaced_slash**: `/` (tap) → ` / ` (double)
- **dt_equal_spaced_equal**: `=` (tap) → ` = ` (double)

### Mod-Morph Behaviors
Keys that change when Shift is held:

- **comma_semicol**: `,` → `;`
- **dot_colon**: `.` → `:`
- **excl_qmark**: `!` → `?`
- **lt_lte**: `<` → `<=`
- **gt_gte**: `>` → `>=`
- **paren_open_closed**: `(` → `)`
- **bracket_open_closed**: `[` → `]`
- **brace_open_closed**: `{` → `}`
- **hash_dollar**: `#` → `$`
- **amp_percent**: `&` → `%`
- **at_caret**: `@` → `^`
- **underscore_cmd**: `_` → Ctrl+Shift+P (Command Palette)
- **slash_pipe**: `/` → `|`
- **backslash_astrk**: `\` → `*`

### Macros

For programming operators with automatic spacing:
- **spaced_equal**: ` = `
- **spaced_equality**: ` == `
- **spaced_unequal**: ` != `
- **spaced_minus**: ` - `
- **spaced_plus**: ` + `
- **spaced_asterisk**: ` * `
- **spaced_slash**: ` / `
- **gte**: `>=`
- **lte**: `<=`

### Sticky Key Configuration
- **Sticky Shift**: 1000ms release-after, quick-release enabled

## Design Philosophy

This configuration is optimized for:
- **Programming**: Quick access to operators with automatic spacing, paired brackets/parens
- **Home row mods**: All modifiers accessible without leaving home position
- **One-handed navigation**: Symmetric navigation options on both hands
- **Minimal finger travel**: Most common operations within one key of home position
- **R language support**: Dedicated assignment operators (`<-`, `|>`)
