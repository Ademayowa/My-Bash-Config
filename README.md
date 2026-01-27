# Bash Configuration

## FZF History Search Function

Add this to your `~/.bashrc` file:

```bash
fh() {
  eval $(history | fzf --tac --tiebreak=index | sed 's/^ *[0-9]* *//')
}
```

### How to Add:
1. Open bash config: `nano ~/.bashrc`
2. Scroll to bottom and paste the function
3. Save: `Ctrl + O`, `Enter`, `Ctrl + X`
4. Reload: `source ~/.bashrc`

### Usage:
```bash
fh
```

This opens an interactive history search. Select a command and it will execute immediately.

### Alternative - Ctrl + R with FZF:
For selecting a command WITHOUT executing (to edit first), add this to `~/.bashrc`:

```bash
eval "$(fzf --bash)"
```

Then use `Ctrl + R` to search history - the selected command will appear in your prompt ready to edit or execute.

## Notes:
- FZF must be installed: `sudo apt install fzf`
- Starship prompt configuration is separate from bash config
- Always reload config after changes: `source ~/.bashrc`


# Tmux Configuration

Enhanced tmux configuration with colored status bar background.

## Configuration

```bash
# Let Starship & terminal colors pass through
set -g allow-passthrough on
# True color support
set -g default-terminal "tmux-256color"
set -ga terminal-overrides ",xterm-256color:Tc"
# Status bar: use a subtle dark background that matches the theme
set -g status on
set -g status-position bottom
# Changed: using a dark gray/charcoal background (#2d2d2d or #1e1e1e work well with dark themes)
set -g status-style bg=#2d2d2d,fg=#a8a8a8
# Left: session name (subtle)
set -g status-left-length 40
set -g status-left "#[bold,fg=#d4d4d4] #S #[default]"
# Right: date & time (clean)
set -g status-right-length 60
set -g status-right "#[fg=#d4d4d4]%Y-%m-%d %H:%M"
# Window tabs (minimal, modern)
setw -g window-status-format " #I:#W "
setw -g window-status-current-format "#[bold,fg=#569cd6] #I:#W "
setw -g window-status-style bg=#2d2d2d,fg=#808080
setw -g window-status-current-style bg=#2d2d2d,fg=#569cd6
```

## Color Options

You can customize the background color by changing the `bg=` value in `status-style`:

- **#2d2d2d** - Default dark gray (recommended)
- **#1e1e1e** - Darker charcoal
- **#3a3a3a** - Lighter gray

## Installation

1. Copy the configuration to `~/.tmux.conf`
2. Reload tmux: `tmux source-file ~/.tmux.conf`
3. Or restart your tmux session

