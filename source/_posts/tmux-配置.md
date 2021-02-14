---
title: tmux 配置
date: 2021-02-07 09:28:05
tags:
- tmux
categories:
- 工具
img: https://blog-cdn.wcmoon.com/tool.jpg
---

个人使用的 tmux 习惯配置。
```
# ~/.tmux.conf
# Send prefix
set-option -g prefix C-a
unbind-key C-a
bind-key C-a send-prefix

# Use shift-arrow keys to switch panes
bind -n S-Left select-pane -L
bind -n S-Right select-pane -R
bind -n S-Up select-pane -U
bind -n S-Down select-pane -D



# Set easier window split keys
bind-key v split-window -h
bind-key h split-window -v

# Easy config reload
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"

# Display color
set -g default-terminal "screen-256color"
```
