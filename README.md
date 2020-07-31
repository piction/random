# random

## Git help

### Get nice logging

==> add 'lognice' as alias (~/.gitconfig)
```
[alias]
  lognice = log --graph  --decorate --format=format:'%C(yellow)%h%C(reset)%C(auto)%d%C(reset) %C(normal)%s%C(reset) %C(dim white)- %an%C(reset) %C(dim blue)(%ar)' --all
```


### Move existing tag to head
```
git push origin :refs/tags/<tagname>
git tag -fa <tagname>
git push origin master --tags
```


## Raspbery PI 

### Finding my pi on the network 

All raspberry devices MAC addresses started with B8:27:EB.
So, on *nix systems, this can be accomplished by executing the following command where 192.168.1.* will be your local network mask
```
sudo nmap -sP 192.168.1.0/24 | awk '/^Nmap/{ip=$NF}/B8:27:EB/{print ip}'
```

### Connecting a Computer to the Pi
Recent versions of Raspbian (which use dhcpcd) allow ssh to work over a link-local address and avahi (which is a zeroconf implementation) enables programs to discover hosts running on a local network.
You can easily connect from Linux and OS X with ssh pi@hostname.local (the default hostname is raspberrypi)
````
ssh pi@raspberrypi.local
````

## Linux

### Compress and extract
````
tar -czvf name-of-archive.tar.gz /path/to/directory-or-file
tar -xzvf archive.tar.gz
`````
* -c: Create an archive.
* -x: Extract archive
* -z: Compress the archive with gzip.
* -v: “verbose” mode -> display progress
* -f: Allows you to specify the filename of the archive.


### bashrc

````
# Colour codes are cumbersome, so let's name them
txtgreen='\[\e[38;5;82m\]' # green
txtpur='\[\e[38;5;99m\]' # Purple
txtyel='\[\e[38;5;226m\]' # Yellow
txtwht='\[\e[0;37m\]' # White
txtrst='\[\e[0m\]' # Text Reset
# Which (C)olour for what part of the prompt?
pathC="${txtgreen}"
gitC="${txtpur}"
pointerC="${txtwht}"
normalC="${txtrst}"
userC="${txtyel}"
# Get the name of our branch , limit the length and put parenthesis around it
gitBranch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/^\(.\{8\}\).*/\1/g' -e 's/* \(.*\)/(\1)/'
}
# Build the prompt
export PS1="${userC}[${debian_chroot:+($debian_chroot)}\u] ${pathC}\W\$ ${gitC}\$(gitBranch)${pointerC}\$${normalC} "

# Update gnome terminal title
function termtitle() {
    # take argument
    TITLE=$1
    shift
    # update title
    PS1='\[\e]0;$TITLE\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
}

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Show contents of the directory after changing to it
function cd () {
  builtin cd "$1"
  ls -ACF
}


alias xclip="xclip -selection c"

cd ~/dev





````




