# dotfiles

Personal shell + tmux configuration for macOS.

## Contents

| Path | What it is |
|---|---|
| `.zshrc` | Zsh config — oh-my-zsh + Powerlevel10k, plugins (`git`, `zsh-autosuggestions`, `zsh-syntax-highlighting`), NVM, fzf, tmux auto-attach, and git-tag helper functions (`gstaging`, `guat`, `gtag`). |
| `.tmux.conf` | tmux config — `C-Space` prefix, vi copy-mode, Alt+hjkl pane nav, floating pickers, theme toggle, TPM + resurrect/continuum session persistence. |
| `.tmux/theme-dark.conf` | TokyoNight Storm theme (dark). |
| `.tmux/theme-light.conf` | Catppuccin Latte theme (light). |
| `scripts/tmux-*` | Helper scripts the tmux keybindings call (session/project/claude/port pickers, session-cache refresh, theme toggle). |

## Install

Symlink the files into place (from the repo root):

```sh
ln -sf "$PWD/.zshrc"      ~/.zshrc
ln -sf "$PWD/.tmux.conf"  ~/.tmux.conf
mkdir -p ~/.tmux ~/scripts
ln -sf "$PWD/.tmux/theme-dark.conf"  ~/.tmux/theme-dark.conf
ln -sf "$PWD/.tmux/theme-light.conf" ~/.tmux/theme-light.conf
for f in scripts/tmux-*; do ln -sf "$PWD/$f" ~/scripts/"$(basename "$f")"; done
chmod +x ~/scripts/tmux-*
```

## Dependencies

Not vendored here — install separately:

- **zsh** with [oh-my-zsh](https://ohmyz.sh/) and [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- zsh plugins: `zsh-autosuggestions`, `zsh-syntax-highlighting`
- [fzf](https://github.com/junegunn/fzf), [nvm](https://github.com/nvm-sh/nvm)
- **tmux** with [TPM](https://github.com/tmux-plugins/tpm) — after linking `.tmux.conf`, launch tmux and press `prefix + I` to install the plugins (`tmux-resurrect`, `tmux-continuum`).

## tmux quick reference

| Binding | Action |
|---|---|
| `C-Space` | prefix |
| `prefix + \|` / `-` | split horizontal / vertical |
| `M-h/j/k/l` | move between panes (no prefix) |
| `prefix + f` | floating session picker |
| `prefix + p` | floating project picker (`~/code`) |
| `prefix + a` | floating Claude-agent picker |
| `prefix + P` | floating port picker |
| `prefix + T` | toggle dark/light theme |
| `prefix + r` | reload config |
