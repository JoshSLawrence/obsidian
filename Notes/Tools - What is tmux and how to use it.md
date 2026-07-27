---
tags:
  - Tools
---
## Quick Start

1. Install [tmux](https://github.com/tmux/tmux/wiki)
2. Install the [tmux package manager](https://github.com/tmux-plugins/tpm)
3. Install the [sensible](https://github.com/tmux-plugins/tmux-sensible) package

> [Tmux Cheat Sheet](https://tmuxcheatsheet.com/)

The goal of the sensible package is to getting a very agreeable starting config.

The tmux config should be created and maintained in `~/.config/tmux/tmux.conf`

## External CLI Commands

All commands will be prefixed with `tmux`.

| Command  | Example                                | Description                                                               |
| :------: | -------------------------------------- | ------------------------------------------------------------------------- |
|  `tmux`  | `tmux`                                 | Create a new tmux session                                                 |
| `source` | `tmux source ~/.config/tmux/tmux.conf` | Reloads config even when in an active session                             |
|  `new`   | `tmux new -s name`                     | Create a new session with the given name. Works in an active session too. |
|   `ls`   | `tmux ls`                              | List running sessions                                                     |
| `attach` | `tmux attach` or `tmux attach -t name` | Attach to last session, or specify session to attach to.                  |

## Hotkeys

Hotkeys and commands can only be executed after enter the *prefix key* `ctrl + b` (default)

| Combination  | Action                                                                                      |
| :----------: | ------------------------------------------------------------------------------------------- |
|     `c`      | Create a new window                                                                         |
|   `number`   | Go to the exact window by its number                                                        |
|     `n`      | Go to the next window                                                                       |
|     `p`      | Go to the previous window                                                                   |
|     `&`      | Close the current window and all it's panes                                                 |
|     `%`      | Horizontally splits the active pane                                                         |
|     `"`      | Vertically Splits the active pane                                                           |
| `arrow keys` | Navigate between panes                                                                      |
|   `{ or }`   | Swap panes                                                                                  |
|     `q`      | Show pane numbers, enter the number to make a given pane active                             |
|     `z`      | Zoom pane to fill the entire window                                                         |
|     `!`      | Turn a pane into a window                                                                   |
|     `x`      | Close a pane                                                                                |
|     `s`      | List running sessions                                                                       |
|     `w`      | Preview sessions, pressing enter will attach you to the session                             |
|     `I`      | Install any missing plugins in your .conf, note the capital `I`. Be sure to `source` after. |

## Session Commands

All session commands will be executed in the tmux command-prompt after entering the prefix key.

| Command        | Example                  | Description                                     |
| -------------- | ------------------------ | ----------------------------------------------- |
| `swap-window`  | `swap-window -s 2 -t 1 ` | Window at index `2` and `1` will swap positions |
| `new`          | `tmux new -s name`       | Create a new session with the given name.       |
| `kill-session` |                          |                                                 |

## Concepts

**Sessions**  - The top-most layer in tmux. A session is a collection of 1 ore more windows manage as a single unit. You can open many sessions at a time, but you will only be "attached" to one at a time.

**Windows** - A container to one or more panes. Only one window will be active at a time within a session.

**Panes** - An individual terminal session. A pane can take up an entire window or be a single split or slice of a window.

## Plugins

- [vim-tmux-navigator](https://github.com/christoomey/vim-tmux-navigator)

## .conf

**24-bit color** - `set-option -sa terminal-overrides ",xterm*:Tc"`
**Catppuccin theme** - `set -g @plugin 'catppuccin/tmux`
**Enable Mouse** - `set -g mouse on`
**Change prefix** -
	`unbind C-b`
	`set -g prefix C-Space`
	`bind C-Space send-prefix`
**Start window nums at 1** -
	`set -g base-index 1`
	`set -g pane-base-index 1`
	`set-window-option -g pane-base-index 1`
	`set-option -g renumber-windows on`
**Split panes open in current working directory** -
	`bind '"' split-window -v -c "#{pane_current_path}"`
	`bind % split-window -h -c "#{pane_current_path}"`
