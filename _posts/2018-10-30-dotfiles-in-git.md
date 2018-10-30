---
layout: post
title:  "Your dotfiles in git"
date:   2017-01-28 22:09:27 +0100
categories: git dotfiles
---

### Versioning your dotfiles

    git init --bare $HOME/.myconf
    alias config='/usr/bin/git --git-dir=$HOME/.myconf/ --work-tree=$HOME'
    config config status.showUntrackedFiles no

Source: https://news.ycombinator.com/item?id=11071754
