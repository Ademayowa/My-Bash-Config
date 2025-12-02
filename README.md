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
