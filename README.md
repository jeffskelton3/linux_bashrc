My current bashrc settings on linux (mint). Take what you want.

```
export NVM_DIR="/home/jskelton/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm

# Hook for desk activation
[ -n "$DESK_ENV" ] && source "$DESK_ENV" || true

# Run twolfson/sexy-bash-prompt
. ~/.bash_prompt

#   ---------------------------
#   TERMINAL UTILITIES
#   ---------------------------

alias s="subl"													  # shortcut to open Sublime Text
alias refresh="echo 'reloading bash settings...' && . ~/.bashrc"  # reload bash configuration
alias dsk="desk ."												  # desk shortcut because I am lazy
alias profile="s ~/.bashrc"										  # shortcut for editing the bashrc file
alias hosts="s /etc/hosts"										  # shortcut for editing the hosts file
alias cp='cp -iv'                           					  # Preferred 'cp' implementation
alias mv='mv -iv'                           					  # Preferred 'mv' implementation
alias mkdir='mkdir -pv'                     					  # Preferred 'mkdir' implementation
alias ll='ls -FGlAhp'                       					  # Preferred 'ls' implementation

#   extract:  Extract most know archives with one command
#   ---------------------------------------------------------
extract () {
    if [ -f $1 ] ; then
      case $1 in
        *.tar.bz2)   tar xjf $1     ;;
        *.tar.gz)    tar xzf $1     ;;
        *.bz2)       bunzip2 $1     ;;
        *.rar)       unrar e $1     ;;
        *.gz)        gunzip $1      ;;
        *.tar)       tar xf $1      ;;
        *.tbz2)      tar xjf $1     ;;
        *.tgz)       tar xzf $1     ;;
        *.zip)       unzip $1       ;;
        *.Z)         uncompress $1  ;;
        *.7z)        7z x $1        ;;
        *)     echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}



#   ---------------------------
#   NETWORKING
#   ---------------------------

alias myip='curl ip.appspot.com'                    # myip:         Public facing IP Address

#   ii:  display useful host related informaton
#   -------------------------------------------------------------------
ii() {
    echo -e "\nYou are logged on ${RED}$HOST"
    echo -e "\nAdditionnal information:$NC " ; uname -a
    echo -e "\n${RED}Users logged on:$NC " ; w -h
    echo -e "\n${RED}Current date :$NC " ; date
    echo -e "\n${RED}Machine stats :$NC " ; uptime
    echo -e "\n${RED}Current network location :$NC " ; scselect
    echo -e "\n${RED}Public facing IP Address :$NC " ;myip
    #echo -e "\n${RED}DNS Configuration:$NC " ; scutil --dns
    echo
}	
```
