---
title: "Introduction to the Command Line"
permalink: /materials/intro-ai-cli/02-command-line
excerpt: "An introduction to the command line and how to work with it"
toc: true
---

## Introducing the Command Line

So far we have been "remotely" working with AI tools through our web browser, but a large part of this course is learning to work "locally" on our computers.

A big piece of that is something called the *Command Line*. The command line is a text-based interface for interacting with your computer. It is also sometimes called the terminal, shell, or console. We will be using the command line a lot in this course, so it is important to get familiar with it. 

Command line sounds very intimidating, but you are probably already familiar with it. For example, have you ever used Windows Explorer or Mac Finder to find and manipulate files? If yes, then the command line is a text-based way of doing the same thing you do with your files.

Command line is particularly popular in coding because we manipulate our code files and run them all in the terminal (something we will discuss more towards the end of the course -- so don't worry if you are on the fence about coding).

## Trying out the Command Line

### Terminals

To interact with the command line, we need to open a terminal. There are many different terminals, and most computers come with one pre-installed.

I recommend downloading iTerm2 [https://iterm2.com/](https://iterm2.com/) for Mac and the new Windows Terminal [https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701) for Windows (for more info about Windows Terminal see [this blog post](https://towardsdatascience.com/new-windows-terminal-the-best-you-can-have-9945294707e7)). You should be able to use both these links to download the appropriate version for your operating system, but **please let the instructor know if you are having problems**.

### Let's do an exercise together

I want to create a new folder (or directory) to hold all the files for this course. I want to call this new folder `is578-2023`.

Let's first create a prompt for ChatGPT to generate a command for us. Here are some of the key points I want to include in my prompt:

- the name of the folder I want to create
- the fact that I want to create this via the terminal
- the location of where I want to create this folder

*Let's brainstorm and discuss results*

----

So know we need to try and understand what ChatGPT is telling us. Let's break down the command:

- `mkdir` is the command to create a new directory
- `is578-2023` is the name of the directory we want to create
- `cd ~` is the location of where we want to create this directory
- `cd` is the command to change directory
- `~` is a shortcut for the home directory
- `pwd` is the command to print the working directory
- `ls` is the command to list the contents of the current directory

*Let's try and run this command in our terminal*

----

Hopefully we've had some success so far and congratulations on completing your first digital experiment! You are officially a digital humanist 🥳!

Now that we are seeing how the command line works, let's try and create a new file in our `is578-2023` directory. In addition to ChatGPT, I would also recommend taking a look at the [command line cheatsheet]({{site.baseurl}}/materials/intro_ai_command_line/03-command-line-cheatsheet.md) to help you with this exercise. 

Let's once again try to generate a prompt to help us create a new file in our `is578-2023` directory. Here are some of the key points I want to include in my prompt:

- the name of the file I want to create
- the fact that I want to create this via the terminal
- the location of where I want to create this file
  

## AI & Command Line Assignment

So far I have been using ChatGPT to generate prompts for us, but now it is your turn to try and generate a prompt.

Download gpt4all https://gpt4all.io/index.html and use it to complete the following assingment:

1. First, using the command line commands and your terminal create a series of nested directories and files.

- At least one your directories needs to have nothing in it.
- At least one of your directories needs to have a file with the text, "You're lost" on it.
- At least one your directories, needs to have a file with the text "You've made it to the center of the maze!"

![maze](https://media.giphy.com/media/Xbn2CXq5u2Wc0/giphy.gif)

2. Try out at least one other AI tool and compare them to the results of gpt4all. 
3. Post your prompt and screenshots of your maze to the GitHub discussion forum [https://github.com/ZoeLeBlanc/is578-intro-dh/discussions/1](https://github.com/ZoeLeBlanc/is578-intro-dh/discussions/1) and share your thoughts on the different AI tools you tried out.

*Remember if you are having trouble to reach out on Slack for assistance!*

## Resources

These are a non-exhaustive list of resources that you can use to learn more about the command line and help you complete the assignment.

1. Ian Milligan and James Baker, "Introduction to the Bash Command Line," Programming Historian 3 (2014), [https://doi.org/10.46430/phen0037](https://doi.org/10.46430/phen0037). This lesson provides a good introduction to the command line, but it is written for Mac and Linux users. Windows users should use the lesson below.
2. Ted Dawson, "Introduction to the Windows Command Line with PowerShell," Programming Historian 5 (2016), [https://doi.org/10.46430/phen0054](https://doi.org/10.46430/phen0054) (this is a good introduction to the Windows command line, which is different from the Bash shell used in the Programming Historian lesson above).
3. Melanie Walsh's Intro to Cultural Analytics Textbook [https://melaniewalsh.github.io/Intro-Cultural-Analytics/01-Command-Line/01-The-Command-Line.html#command-line-cheatsheet](https://melaniewalsh.github.io/Intro-Cultural-Analytics/01-Command-Line/01-The-Command-Line.html#command-line-cheatsheet)
5. [Bash Basics Part 1 of 8 | Access and Navigation](https://youtu.be/eH8Z9zeywq0?t=885)
6. [Beginner's Guide to the Bash Terminal](https://www.youtube.com/watch?v=oxuRxtrO2Ag)
7. [The Most Important Thing You'll Learn in the Command Line](https://www.youtube.com/watch?v=q7-aEspwwEI)
8. Go through the CodeAcademy [command line course](https://www.codecademy.com/learn/learn-the-command-line).
9. [Shell Scripting Tutorial](https://www.youtube.com/watch?v=hwrnmQumtPw)

## In-Depth Intro to the Command Line and Shells

![command-line](https://image.slidesharecdn.com/cli-101-170406170732/95/commandline-101-3-638.jpg?cb=1491498863)

This is a helpful but brief overview. Often you might get confused, because we'll talk about command line interface/CLI, terminal, shell, console. While these terms are overlapping, my colleague [Shane Lin at UVA](https://github.com/scholarslab/CodeLab/blob/master/Week01/commandline.md) helped me understand that a lot of the differences between these terms has to do with the history of early computers, when computers looked like this 👇🏽.

![early-computer](https://www.computerhope.com/cdn/eniac.jpg)

According to Shane,
> Operators would interact with these machines through a smaller device dedicated to input and output, called a console or terminal. In the very early days, these consoles would use literal printers to print out output from the computer onto paper. In modern computing, "console" and "terminal" are analogies for software programs that replicate these technologies. The application "Terminal" on MacOS is a terminal software.

> A "shell" is a program that lives within a terminal that interprets commands from users and parses output from the computer. The name Shell comes out of the influential Unix operating system and is intended to convey the idea that shell programs completely surround and hide away the complex details of different underlying computer systems from users to provide a simplified and common interface. BASH (Bourne Again SHell) and Zsh (Z Shell) are the most popular shell programs.

To give even more depth, at its base, a shell is simply a macro processor that executes commands. The term macro processor means functionality where text and symbols are expanded to create larger expressions.

A bash shell is both a command interpreter and a programming language. As a command interpreter, the shell provides the user interface to the rich set of utilities for your operating system. The programming language features allow these utilities to be combined. Files containing commands can be created, and become commands themselves. These new commands have the same status as system commands in directories such as /bin, allowing users or groups to establish custom environments to automate their common tasks.

Shells may be used interactively or non-interactively. In interactive mode, they accept input typed from the keyboard. When executing non-interactively, shells execute commands read from a file.

Shells also provide a small set of built-in commands (builtins) implementing functionality impossible or inconvenient to obtain via separate utilities. For example, cd, break, continue, and exec cannot be implemented outside of the shell because they directly manipulate the shell itself. The history, getopts, kill, or pwd builtins, among others, could be implemented in separate utilities, but they are more convenient to use as builtin commands. All of the shell builtins are described in subsequent sections.

While executing commands is essential, most of the power (and complexity) of shells is due to their embedded programming languages. Like any high-level language, the shell provides variables, flow control constructs, quoting, and functions.

Shells offer features geared specifically for interactive use rather than to augment the programming language. These interactive features include job control, command line editing, command history and aliases.





