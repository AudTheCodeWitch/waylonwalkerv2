---
templateKey: blog-post
path: keyboard-driven-vscode
title: Keyboard Driven VSCode
date: 2019-07-07T05:00:00Z
status: published
description: Reimagining my tmux configuration inside of vscode.
cover: "/static/images/alt b.png"
twitter_cover: "/static/images/alt b.jpg"

---
> Throw that mouse Away its time to setup some keyboard shortcuts.

These sortcuts were the baseline for switching from tmux/vim to vscode.  Most folks posts I was able to find gave great tips on replacing vim, but very few have focused on the hackability of tmux.  tmux allows me to rapidly fire up a workspace, create new windows and splits.  Then When I switch tasks I can leave that workspace open and and jump right back in later exactly where I left off.  There is nothing quite like it.  The shortcuts listed here make the transition a bit better. The worst thing I found when using vscode at first was no way to switch between the terminal and editor without the mouse.  This first set of keybindings solve that issue.

> The worst thing I found when using vscode at first was no way to switch between the terminal and editor without the mouse.

## Alt+\[hjkl\]

_navigation_

⬅ jump to **left** split **alt+h**

⬇ jump to **terminal** from editor **alt+j**

⬆ jump to **editor** from terminal **alt+k**

➡ jump to **right** split **alt+l**

This is by var the most useful set of keybindings that I use in vscode and is directly replicated from my tmux configuration.  It allows me to quickly jump up, down, left, right.  Do note that if you use vertical splits it does not work as well as tmux 😢.

![navigating vscode with keyboard shortcuts](/images/alt \[hjkl\].gif "Alt+[hjkl]")

    [
            {
                "key": "alt+j",
                "command": "workbench.action.terminal.focus",
                "when": "editorFocus"
            },
        
            {
                "key": "alt+k",
                "command": "workbench.action.focusFirstEditorGroup",
                "when": "terminalFocus"
            },
            {
                "key": "alt+k",
                "command": "workbench.action.focusAboveGroup",
                "when": "editorFocus"
            },
            {
                "key": "alt+l",
                "command": "-toggleFindInSelection",
                "when": "editorFocus"
            },
            {
                "key": "alt+l",
                "command": "workbench.action.focusNextGroup",
                "when": "editorFocus"
            },
            {
                "key": "alt+h",
                "command": "workbench.action.focusPreviousGroup",
                "when": "editorFocus"
            },
        
            {
                "key": "alt+l",
                "command": "workbench.action.terminal.focusNextPane",
                "when": "terminalFocus"
            },
            {
                "key": "alt+h",
                "command": "workbench.action.terminal.focusPreviousPane",
                "when": "terminalFocus"
            },
    ]

## Alt+b

_toggle bloat_

Since closing the sidebar is assigned to `ctrl+b` I thought that it made most sense to simulate the activity bar with `alt+b`.  There are many times when I just want to get as much out of the way as possible and this little bit does help.

![hiding the activity bar ](/images/alt b.gif "Alt+b")

    [
        {
            "key": "alt+b",
            "command": "workbench.action.toggleActivityBarVisibility",
            "when": "editorFocus"
        },
    ]

## Alt+\[svx\]

_Split it up_

🙌 Split hoizontally **alt+s**

🍌 Vertically **alt+v**

💥 Close **alt+x**

This is another one replicated from tmux for quickly creatiting horizontal (s) and vertical (v) splits.  Once I am done with them I can close them with alt+x.

![Make and destroy splits with ease in vscode.](/images/alt \[svx\].gif "spliting the editor")

     [
        {
            "key": "alt+s",
            "command": "workbench.action.terminal.split",
            "when": "terminalFocus"
        },
        {
            "key": "alt+s",
            "command": "workbench.action.splitEditor",
            "when": "editorFocus"
        },
        {
            "key": "alt+v",
            "command": "workbench.action.splitEditorOrthogonal",
            "when": "editorFocus"
        },
        {
            "key": "alt+x",
            "command": "workbench.action.terminal.kill",
            "when": "terminalFocus"
        },
        {
            "key": "alt+x",
            "command": "workbench.action.closeActiveEditor",
            "when": "editorFocus"
        }
      ]

## Alt+\[cnp\]

🤲 **Create** new workspace **alt+c**

⏭ jump to **next** workspace **alt+n**

⏮ jump to **previous** workspace **alt+p**


Sometimes the terminal window gets a bit cramped inside of splits and you need to use different panes.  I replicated the cnp pattern from tmux here as well.  I can create (c) new panes, then go to the next (n), or previous (p) without leaving the comfort of my keyboard.

I am often using this one when I have a process running that I watch like gatsby, and I need to quickly pop into a new pane to run a git command and back in to gatsby before jumping up to my editor.

![](/images/alt \[cnp\].gif)

    [
        {
            "key": "alt+c",
            "command": "workbench.action.terminal.new",
            "when": "terminalFocus"
        },
        {
            "key": "alt+n",
            "command": "workbench.action.terminal.focusNext",
            "when": "terminalFocus"
        },
    
        {
            "key": "alt+p",
            "command": "workbench.action.terminal.focusPrevious",
            "when": "terminalFocus"
        },
    ]

## Alt+z

🗻 Zoom into terminal **alt+z**

This last one doesnt work as well as I would like but it sure does get the job done.  It Zooms (z) into the terminal from anywhere in vscode.  I can be in my editor and zoom out of the terminal to make more room, or zoom in to see what happened from my last edit.

![](/images/alt z.gif)

    [
        {
            "key": "alt+z",
            "command": "workbench.action.toggleMaximizedPanel",
        },
    ]