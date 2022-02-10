---
title: Customize your linux terminal with .bashrc
description: This is a post about customzing your linux terminal with the ./bashrc file
draft: false
date: 2022-02-10T20:29:22+01:00
tags: [programming, linux, bash]
---

## What is .bashrc

`.bashrc` is a file that lies in your home directory. It executes on terminal bootup and refreshing. It is written in bash. You can use it to customize your terminal in different ways.

## Echo ascii text

One of the simplest things you can do with `.bashrc` is to echo ascii text on bootup. For that you open `.bashrc` with your editor of choice, I'm using `sudo vi ~/.bashrc`

You can now use the `echo` command at the end of the file. In my `.bashrc` I used 
```bash
echo "     _________         _____         __           _______                 "
echo "    /   _____/_____   /  |  |_______|  | _____.__.\   _  \   ____   ____  "
echo "    \_____  \\____ \ /   |  |\_  __ \  |/ <   |  |/  /_\  \ /    \_/ __ \ "
echo "    /        \  |_> >    ^   /|  | \/    < \___  |\  \_/   \   |  \  ___/ "
echo "   /_______  /   __/\____   | |__|  |__|_ \/ ____| \_____  /___|  /\___  >"
echo "           \/|__|        |__|            \/\/            \/     \/     \/ "
```
This will now be written on bootup or refresh at the beginning of your terminal. You can refresh using `source .bashrc`

## Create custom commands

You can also define custom commands using the `alias` command. You can for example create the command `helloworld` that prints "hello" and then "world" like so
```bash
alias helloworld="echo hello; echo world;"
```
This command can then be used, as soon as you refresh your terminal.

These commands can be complex as you want and can also e.g. take input using `read`.<br>

## Customizing your prompt

Your current prompt probably looks something like this `username@hostname:directory$`. 

If you want to have the option to color the prompt later, go into `.bashrc`, find `#force_color_prompt=yes` and change it to `force_color_prompt=yes`.

We will now change the prompt using the `PS1` variable. You can view the current `PS1` configuration through `echo PS1`. I would recommend saving that configuration for backup in a default variable through executing `DEFAULT=$PS1` in the terminal. 

To customize PS1 you should remember that 
- `\u` indicates the username of the current user
- `\h` indicates the hostname of the current user
- `\w` indicates the working directory
- `\$` indicates whether you are a normal user ($) or the root user (#).
There also other, but I'm not going to cover them. You can now set 
```bash
PS1="\u\$"
``` 
through the terminal to make the change temporary or in `.bashrc` to make the change permanent. After refreshing your prompt will look like `username$`.

You can also add color tags to make all text after the tag colored that color. That can be done like this `\[\033[<colorcode>m\]` the color code can be e.g. one of the following.
- Green: 32
- Red: 31
- Black: 30
- Blue: 34
- Cyan: 36
- Purple: 35
- Yellow: 33
- White: 37

You can also add an attribute to the color tag, which will style the text. That will look like this `\[\033[<attribute>; <colorcode>m\]`. The attribute can be one of the following.
- Normal: 0
- Bold (ubuntu): 1
- Dim: 2
- Underlined: 4
- Blinking: 5
- Text- and backgroundcolor reversed: 7
- Hidden text: 8

I customized my prompt with 
```bash
PS1="\[\033[34m\]\u\[\033[1;34m\]@\[\033[0;34m\]\h:\[\033[1;34m\]\w\[\033[0;37m\]\$ "
```