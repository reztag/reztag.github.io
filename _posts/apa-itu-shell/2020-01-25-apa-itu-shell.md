---
title: What is a shell? 🐚 is it a magical shell?
date: 2020-01-25 11:58:47 +07:00
modified: 2020-02-02 16:49:47 +07:00
tags: [unix/linux, cli]
description: A shell is a command-line interpreter; a program that acts as a translator for commands inputted by the user through the terminal, so that the commands can be understood by the Kernel.
image: "/apa-itu-shell/shell_evolution.png"
---

<a href="http://www.youtube.com/watch?v=tc4ROCJYbm0&t=70" target="_blank" rel="noopener">In the past</a>, before the existence of a <abbr title="Graphical User Interface">GUI</abbr>, users interacted with computers using a <abbr title="Command Line Interface">CLI</abbr> by typing command lines in a text-based interface like this 👇.

<figure>
<img src="/apa-itu-shell/terminal_nginx.gif" alt="installing nginx in ubuntu">
<figcaption>Fig 1. Terminal emulator, package installation, and service check.</figcaption>
</figure>

If you have ever used Unix/Linux, you might have used the program above, and maybe even use it every day to execute a command through a <a href="http://en.wikipedia.org/wiki/List_of_terminal_emulators" target="_blank" rel="noopener">terminal emulator</a>.

Users<sup id="user">[[1]](#user-ref)</sup> cannot directly communicate with computer hardware, so we need an operating system; the **Kernel** is a program that serves as the core of the computer's operating system.

<figure>
<img src="/apa-itu-shell/kernel.png" alt="kernel central of operating system">
<figcaption>Fig 2. Kernel diagram.</figcaption>
</figure>

The Kernel facilitates the interaction between hardware and software components, handling input/output requests from software and translating them into data processing instructions for the CPU, so that the hardware (CPU, memory, devices) understands the user's intended commands.

When we input a command in the terminal emulator, the kernel doesn't immediately understand the command we type. We need an interface as an intermediary to the kernel, and that interface is called the **Shell**.

<figure>
<img src="/apa-itu-shell/shell.png" alt="shell">
<figcaption>Fig 3. Shell communication diagram.</figcaption>
</figure>

<mark>A shell is a command-line interpreter; a program that acts as a translator for commands inputted by the user through the terminal</mark>, so that the commands can be understood by the Kernel.

The login shell is usually set by the local System Administrator when the user is first created. You can see the login shell you are currently using with the following command.

```bash
$ echo $SHELL
# or
$ echo $0
```

Each shell has a default prompt. Here are some of the most common shells:

```bash
$ (dollar sign)   # sh, ksh, bash
% (percent sign)  # csh, tcsh
```

##### Terminology in shell prompt

The shell prompt is where we write a command. Here are the terminologies that can help you understand its parts.

<figure>
<img src="/apa-itu-shell/term_shell_prompt.png" alt="shell">
<figcaption>Fig 4. Parts of a shell prompt.</figcaption>
</figure>

Below is an example of a simple command to display the CPU architecture of the computer I am currently using.

<figure>
<img src="/apa-itu-shell/terminal_lscpu.gif" alt="installing nginx in ubuntu">
<figcaption>Fig 5. Displaying information about the CPU architecture.</figcaption>
</figure>

From the example command, when a user types an input command in the terminal and presses <kbd>ENTER</kbd>, the shell will transform the user's command into a language that can be understood by the kernel. The kernel then translates it into data processing instructions for the hardware, resulting in the appropriate output based on the user's command.

Shells have various types and derivatives. Here are some of the most common ones.

<figure>
<img src="/apa-itu-shell/shell_evolution.png" alt="shell evolution">
<figcaption>Fig 6. Shell evolution over the years.</figcaption>
</figure>

A brief explanation of the image above:

- Bourne shell `sh`
  Developed by Stephen Bourne at Bell Labs, which at the time replaced Thompson shell (created by Ken Thompson). Many Unix-like systems still have `/bin/sh`—which may be a symbolic link or hard link—pointing to it, even when other shells are used, as compatibility for commands.
- Korn shell `ksh` Unix shell developed by David Korn at Bell Labs. The development is based on the source code of the Bourne shell, but it also has features from `csh` and `sh`. Its development is still actively maintained <a href="http://github.com/att/ast" target="_blank" rel="noopener">here</a>.
- Bourne again shell `bash`
  This is an open-source project by the <a href="http://gnu.org/software/bash/" target="_blank" rel="noopener">GNU project</a>. It is compatible with `sh` and combines important features from `ksh` and `csh`. It is one of the most commonly used shells (usually the default login shell for Linux and Apple's macOS Mojave).
- Z shell `zsh` has its own community called <a href="http://ohmyz.sh/"  target="_blank" rel="noopener">"Oh My Zsh"</a>. `zsh` plugins and themes can be found in this community. I am currently using `zsh`, which is also the default shell in macOS Catalina, replacing bash.
- friendly interactive shell `fish`
  As described on its <a href="http://fishshell.com/" target="_blank" rel="noopener">website</a>, this shell is fun. One feature I like about this shell is the autosuggestions and easy configuration through a web-based interface.

There is still much more to explain in this article. If you are still interested, read more <a href="http://en.wikipedia.org/wiki/List_of_command-line_interpreters#Operating_system_shells" target="_blank" rel="noopener">here</a> and also compare each shell <a href="http://en.wikipedia.org/wiki/Comparison_of_command_shells" target="_blank" rel="noopener">here</a>.

If you are interested in changing the default login shell in your operating system, you can install it by following the documentation/installation instructions for each shell. I won't cover it here because the distribution you are using may vary.

To set the default login shell in the OS, you can use this command.

```bash
# command
$ sudo chsh [options] [LOGIN]

# example usage
$ sudo chsh -s /user/bin/zsh harpi
# change the default shell for the user "harpi" to zsh shell.
$ reboot

# or you can also manually edit the /etc/passwd file to change the user's shell.
# If you are still confused, use the `man` command to view the manual page.
$ man chsh
```

Finally, for this article, shells have various types, so choose the shell that suits your preferences to enhance productivity and adjust it to your needs. Having too many plugins and being confused about choosing a theme is not good 😁.

Thank you for reading. _The author welcomes criticism and suggestions._

##### Notes

<small id="user-ref"><sup>[[1]](#user)</sup> Humans who operate and control computer systems.</small>

##### Resources

- [Evolution shells in Linux](http://developer.ibm.com/tutorials/l-linux-shells/)
- [Kernel Definition](http://www.linfo.org/kernel.html)
- [The Shell](http://www.cis.rit.edu/class/simg211/unixintro/Shell.html)

