
#### The apps

..I think these all apps I've downloaded using apt.


```yml
aria2c
firewalld
firewall-config
emacs
emacs-nox
chromium
qemu
virt-manager
cmake
```



<br><br><br>

#### obtain sources.list and sources.list.d/


```bsh
# deb cdrom:[Debian GNU/Linux 11.6.0 _Bullseye_ - Official amd64 DVD Binary-1 20221217-10:40]/ bullseye contrib main

# deb cdrom:[Debian GNU/Linux 11.6.0 _Bullseye_ - Official amd64 DVD Binary-1 20221217-10:40]/ bullseye contrib main

deb http://mirrors.ocf.berkeley.edu/debian/ bullseye main non-free contrib
deb-src http://mirrors.ocf.berkeley.edu/debian/ bullseye main non-free contrib

deb http://security.debian.org/debian-security bullseye-security main contrib non-free
deb-src http://security.debian.org/debian-security bullseye-security main contrib non-free

# bullseye-updates, to get updates before a point release is made;
# see https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_updates_and_backports
deb http://mirrors.ocf.berkeley.edu/debian/ bullseye-updates main contrib non-free
deb-src http://mirrors.ocf.berkeley.edu/debian/ bullseye-updates main contrib non-free


deb https://deb.debian.org/debian experimental main
```



<br><br><br>

#### ~/.bashrc


```bsh
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
#[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    alias dir='dir --color=auto'
    alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi


alias czc="cat /dev/null"
alias cls="clear ;"
alias CLS="clear ;"
alias LSL="ls -las"
alias LSS="sudo ls -las"
alias lsl="ls -las"
alias lss="sudo ls -las"
alias aptu="sudo apt update; echo -e 'apt update \\n';"
alias aptuu="sudo apt-get update; echo -e 'apt-get update \\n'; sudo apt update; echo -e 'apt update \\n';"
alias app="echo -e 'sudo apt install \\n'; sudo apt install"
alias aps="apt search"
alias apss="apt show"
alias aptl="apt list --installed"
alias apli="apt list --installed"
alias apl="apt list --installed"
alias ~="cd ~"
alias ~~~="source ~/.bashrc"
alias ~~~~~="vim ~/.bashrc"
alias ..="cd .."
alias ...="cd ..;cd ..;"
alias ....="cd ..; cd..; cd ..;"
alias .....="cd ..;cd ..;cd ..;cd ..;"
alias ......="cd ..; cd ..; cd ..; cd ..; cd ..;"
alias .,="cd .."
alias .,.,="cd ..;cd ..;"
alias .,.,.,="cd ..; cd ..; cd ..;"
alias .,.,.,.,="cd ..;cd ..;cd ..;cd ..;"
alias gg="gzip -dklrtv"
```
