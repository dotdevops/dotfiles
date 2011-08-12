This is my collection of .files
=================================

This configuration will work if you have RVM + use git
If you do not use git change the prompt to be something more fun

CHANGE:
=======
    export PS1="${USER} : \[\033[01;34m\]\$(~/.rvm/bin/rvm-prompt) \[\033[01;32m\]\w\[\033[00;33m\]\$(__git_ps1 \" (%s)\") \[\033[01;36m\]\$\[\033[00m\] "

TO:
===
    function elite
    {
     GRAY="\[\033[1;30m\]"
     LIGHT_GRAY="\[\033[0;37m\]"
     YELLOW="\[\033[0;33m\]"
     RED="\[\033[1;31m\]"
    WHITE="\[\033[1;37m\]"
     D_COLOR="\[\033[00;37m\]"
    case $TERM in
        xterm*)
            TITLEBAR="\[\033]0;\u@\h:\w\007\]"
            ;;
        *)
            TITLEBAR=""
            ;;
    esac
    GRAD1=$(tty|cut -d/ -f3)
    PS1="$TITLEBAR\

    $RED{\
    $WHITE\u$RED@$WHITE\h\
    $RED} [ \
    $YELLOW\$(date +%H:%M)$GRAY/$YELLOW\$(date +%d-%b-%y)\
    $RED ]\
    \n\
    $RED< \
    $RED\w\
    $RED >$D_COLOR "
    PS2="$RED-$RED-$WHITE"
    }

    if [ ${SHELL##/*/} = "bash" ] ; then
         if [ $TERM = x"term" ] ; then
                        HOSTNAME=`uname -n`
                        label () { echo -e "\033]2;$*\007\c"; }
                        alias stripe='label $LOGNAME on $HOSTNAME - ${PWD#$HOME/}'
                        cds () { "cd" $*; eval stripe; }
                        alias cd='cds'
                        eval stripe
                        export PS1='\$ '
            fi
    fi

    elite

