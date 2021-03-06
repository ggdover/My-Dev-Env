
## Cheat sheets

#### [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
e.g. .md files, Like this one! :D

#### [Powershell](https://cdn.comparitech.com/wp-content/uploads/2018/08/Comparitech-Powershell-cheatsheet.pdf)
e.g. .ps1 files, could also be commands to be typed directly in powershell console

## Version control tips and trix

What each branch means in 3-way merge:
* Left = From/Other branch/Incoming
* Right = To/Local branch/Destination
* Base = Where "Left" and "Right" diverged

## Stand-alone keyboard shortcuts

### Platform independent

* Hold `cmd⌘` or `ctrl` and press left or right arrow key to jump text-marker to beginning or end of a line in a text editor. Can be used in conjunction with `shift`

### Mac/OSX

* In Chrome webbrowser, to open a link in new window: Hold `cmd⌘` while clicking the link.

## Stand-alone command line tricks

* To read command line arguments form a file
by piping them. For example:
the argument ARGS is stored in txt-file namned
FILE.txt and will be piped to as an argument to the command COMMAND. In the command prompt write:
```echo < FILE.txt | COMMAND```
Which will result in:
```COMMAND ARGS```

## Google chrome extensions

#### [Github repository size](https://chrome.google.com/webstore/detail/github-repository-size/apnjnioapinblneaedefcnopcjepgkci/related?ref=producthunt)
Ability to view size of repository on github in webbrowser before cloning it.
[Link](https://stackoverflow.com/questions/8646517/see-the-size-of-a-github-repo-before-cloning-it) to stackoverflow thread that guided me to the extension

## Sublime keybindings

Copy-paste into "Preference->Key bindings"

```
[
	{ "keys": ["ctrl+e"], "command": "toggle_side_bar" },
	{ "keys": ["alt+z"],  "command": "toggle_setting", "args": {"setting": "word_wrap"}}
]
```

## Visual code keymaps

### Defaults:
* Ctrl + Space = Show suggest/auto-complete dropdown menu (OBS! Make sure textmarker is in the right place, next to parentheses or other token)


## Cmder (terminal emulator for Windows)

[Link to repo](https://github.com/cmderdev/cmder)<br/>
[Link to website](https://cmder.net/)

## iTerm (terminal emulator for OSX)

## Raspberry pi (Raspian)

#### Hotkey/keyboard shortcuts

To resize window = Alt + space (Will give you a dropdown menu with several options to resize window, navigate with arrow keys) ([Source](https://raspberryinsider.com/top-15-raspberry-pi-keyboard-shortcuts/))

#### GPIO Uart

If GPIO Uart doesn’t work, make sure you add ‘enable_uart=1’ at the bottom in the file ‘/boot/config.txt’ ([Source](https://elinux.org/RPi_Serial_Connection))

#### GPIO pinout/pin-info

Enter ‘pinout’ or if that doesn’t work, try ‘gpio readall’ to get info about each pin on the GPIO (e.g. which one is 5/3.3V, GND, uart, i2c etc. etc.) [Here is also a nice link for info on the GPIO](https://pinout.xyz/) (FYI The link is referenced/mentioned on raspberry pi’s official website)

## gitk (Gui client)

Comes with the installation of git on the computer. Type `gitk` from terminal
to open working directory as repository in gitk.

#### Dark theme for gitk

[Website](https://draculatheme.com/gitk/)</br>
[Repository](https://github.com/dracula/dracula-theme/)

#### Custom theme

There is a file namned **gitk** in **~/.config/git/** (on osx atleast).
This is the config for setting styling in gitk, basically the current theme.
Here is a list of the settings that I know exists with clarification on what
each row actually controls since it's difficult to figure this out by its name.

I'm planning to add commens continually until every row/setting is clarified.

set mainfont {{Lucida Grande} 5}
>Font of text in windows that list commit history (incl. author and date) and the window listing files affected in selected commit

set textfont {Monaco 10}
>Font of text in diff-display window, commit (sha1) hash and row number for selected commit in commit history window

set uifont {{Lucida Grande} 25 bold}
>Font of title text for radio buttons and text fields  

set tabstop 8  
set findmergefiles 0  
set maxgraphpct 50  
set maxwidth 16  
set cmitmode patch  
set wrapcomment none  
set autoselect 1  
set autosellen 40  
set showneartags 1  
set maxrefs 20  
set visiblerefs {"master"}  
set hideremotes 0  
set showlocalchanges 1  
set datetimeformat {%Y-%m-%d %H:%M:%S}  
set limitdiffs 1  
set uicolor #181915  
set want_ttk 0  
set bgcolor #282923  
set fgcolor #f8f8f2  
set uifgcolor #f8f8f2  
set uifgdisabledcolor #6272a4  
set colors {#50fa7b #ff5555 #bd93f9 #ff79c6 #f8f8f8 #ffb86c #ffb86c}  
set diffcolors {#ff5555 #50fa7b #bd93f9}  
set mergecolors {#ff5555 #bd93f9 #50fa7b #bd93f9 #ffb86c #8be9fd #ff79c6 #f1fa8c #8be9fd #ff79c6 #8be9fd #ffb86c #8be9fd #50fa7b #ffb86c #ff79c6}  
set markbgcolor #282a36  
set diffcontext 3  
set selectbgcolor #44475a  
set foundbgcolor #f1fa8c  
set currentsearchhitbgcolor #ffb86c  
set extdifftool opendiff  
set perfile_attrs 0  
set headbgcolor #50fa7b  
set headfgcolor black  
set headoutlinecolor #f8f8f2  
set remotebgcolor #ffb86c  
set tagbgcolor #f1fa8c  
set tagfgcolor black  
set tagoutlinecolor #f8f8f2  
set reflinecolor #f8f8f2  
set filesepbgcolor #44475a  
set filesepfgcolor #f8f8f2  
set linehoverbgcolor #f1fa8c  
set linehoverfgcolor black  
set linehoveroutlinecolor #f8f8f2  
set mainheadcirclecolor #f1fa8c  
set workingfilescirclecolor #ff5555  
set indexcirclecolor #50fa7b  
set circlecolors {#282a36 #bd93f9 #44475a #bd93f9 #bd93f9}  
set linkfgcolor #bd93f9  
set circleoutlinecolor #44475a  
set geometry(main) 840x1005+5+23  
set geometry(state) normal  
set geometry(topwidth) 838  
set geometry(topheight) 355  
set geometry(pwsash0) "401 1"  
set geometry(pwsash1) "616 1"  
set geometry(botwidth) 412  
set geometry(botheight) 638  
set permviews {}  

## Setting up dev environment on Windows

* Suggested package manager = Chocolatey
* Suggested terminal to get UNIX commands/tools = Gitbash terminal for windows
(An alternative is to use WSL (Windows Subsystem for Linux))
* Install Visual code
* To move/resize windows, use the WinKey + arrow keys
* Disable the annoying 'Aero snap' in windows 10 (Whenever you move a window it will sort of float the windows and wait for you to click one window for it to be selected/focused. TODO: add instructions for how to disable it)
* To change drive in cmd.exe, just type drive-letter followed by ':', so for example 'C:'. In 'Git bash' however, you do 'cd' + space + drive letter, from root, so for example: 'cd /c' or if you're already in root folder simply 'cd c'
* Check out cscript and wscript to get help on how the script-lingo of cmd.exe works, e.g. options for commands etc. (TODO: What is the difference between wscript and cscript??)
* To access environment variable in powershell = '$env:' + 'name of environment variable', so for example: "echo $env:PATH"
* To access environment variable in cmd.exe = '%' + 'name of environment variable' + '%', so for example: "echo %PATH%"
* Powershell, how to set/append to environment variable, example:
  * $env:Path = "SomeRandomPath";             (replaces existing path) 
  * $env:Path += ";SomeRandomPath"            (appends to existing path)

# Virtualbox Tips

## Black screen when making size of screen bigger

Solution might be to simply increase the video memory.</br>
Shut off your current session of virtualbox guest and increase the video memory significantly.</br>
Then start guest again and see if it got fixed

## Setup a static ip, so you can ssh from Host OS to Guest OS

The following guide that I wrote for work describes how to do this.
Can be found in a seperate Markdown file, [click this link](virtualbox_static_ip_guest_and_ssh.md).
(If the link doesn't work. The file your looking for is in this repository
 and is namned virtualbox_remote_host_to_guest.md)
