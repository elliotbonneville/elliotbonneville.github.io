---
layout: post
title: How To Use Vim as a Text Editor
comments: true
permalink: how-to-use-vim-as-a-text-editor
---

So in my [last post](hello-world), I mentioned that I would be writing in either the Github Code editor or my text editor of choice, Vim.

Well, after thinking about it more, I've decided that I like the idea of being able to stay in Vim a lot, and also I don't want to go gallivanting about the internet every time I want to write a new post. So, I'm going to be writing in Vim.

Problem is, I have it set up to write code, not text.

<!--break-->

Here's a screenshot of what it looks like right now:

![Vim set up for code editing](/public/vim-for-code-editing.png)

So there are clearly a few problems here:

### Lines wrap far past the 80 character limit

I set up a nice ruler at the 80 character mark using `set colorcolumn=80`. It would be nice if we could get my lines to soft-wrap at that 80 character mark instead of at the window width.

### Actually, let's get rid of that 80 character mark entirely

We want text to soft wrap there. We don't want the ruler at all for writing text. For writing code, it's helpful because I need to know when to break the lines manually, but prose doesn't flow that way at all.

### Can we turn off the line count?

I don't need to see how many lines my text file is, because again that's something irrelevant to prose. Yes, it's still useful for goto commands, but I find myself using search commands more to navigate my text than goto's,  because we have many wrapped lines and you can only jump to the beginning of a line with a direct goto.

### Moving up and down soft-wrapped lines will be annoying

Vim treats soft-wrapped lines as single lines, so navigating up and down them with the `j` and `k` keys will skip everything after the line wraps. In other words, it only navigates original lines, not _displayed_ lines.

Luckily, there's [a way to fix that](http://vim.wikia.com/wiki/Move_cursor_by_display_lines_when_wrapping), which I did a while ago, since it's sometimes useful in code contexts, typically with long lines of HTML, etc.

*tl;dr:* All you have to do is remap `j` and `k` to `gj` and `gk`:

```
nmap j gj
nmap k gk
```

Now Vim treats even wrapped lines like regular lines.

### Fixing this

My initial approach was to start writing a function that did all the above manually. I started in on it and quickly found things were more complicated than I'd thought. For example, I wanted to hide the line bar, but when I did that the words ran right to the edge of the terminal, and that looked gross.

In the process of researching that I came across some neat plugins, namely [Goyo](https://github.com/junegunn/goyo.vim) and [Limelight](https://github.com/junegunn/limelight.vim), both by [Junegunn Choi](https://github.com/junegunn), who is a Vim-master.

I installed those plugins (I use Vundle as a package manager) and dropped in a few lines to integrate them into my current configuration:

```
nmap <Leader>l :Goyo<Enter>
autocmd! User GoyoEnter Limelight
autocmd! User GoyoLeave Limelight!
```

They're so simple it's barely worth mentioning, but I didn't want this post to be completely anticlimactic. 

Here's the result, with my current configuration:

![Vim with Goyo and Limelight](public/vim-with-goyo-and-limelight.gif)

### One more thing

If you notice, lines will sometimes break in the middle of a word. There's a Vim setting to fix this, of course: `:set linebreak`.

Since I always break lines of code manually before or when they reach the 80 character limit, I'm comfortable setting this as a global setting, even outside of writing mode. The alternative would be to bind it to whenever Goyo is entered or left as I've done with Limelight, but it's unnecessary right now. So I'm just going to go ahead and drop that line right in my `.vimrc`.

So there you have it -- now I can use Vim to write offline, and it looks great, too.

🎉
