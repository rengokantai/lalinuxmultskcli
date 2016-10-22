# lalinuxmultskcli
##1. Processes in Linux
###2 Foreground and background tasks
####00:58
[meanings of signals](http://programmergamer.blogspot.com/2013/05/clarification-on-sigint-sigterm-sigkill.html)
SIGSTP ; ctrl z (suspend a process)  
to resume a suspended process (in gackground)
```
bg %1
```
bring this to forefround
```
fg %1
```
or
```
%1
```


####03:00
create a big file
```
fallocate -l 4GB filename
```
send this file using scp, we cannot use & because it requires password.Hence the step should be    
```
scp filename user@ip:/location
password:
(ctrl z)
bg %1
```
####04:49 suspend vim
ctrl z (non-edit mode)


###3 Control more than one process
####01:17 + -
```
jobs
```
The plus indicates the most recently backgrounded process, and the minus represents the previously backgrounded process.  
bring recently background precess to foreground:
```
fg
```
bring previous one
```
fg -
```
####02:13
let a stopped process run in gackground (recent one) just
```
bg
```
multiple jobs run same time
```
bg %4 %5
```








###4 Processes and jobs
Jobs is a bash built-in, so its specific documentation is available through help, rather than man. 
```
help jpbs
```
####01:15
show pids
```
jobs -l
```
suspend
```
kill -stop 1234  / kill -stop %2
```
continue
```
kill -cont 1234
```
remove from joblist
```
disown %5
```
this process is still running. verify
```
ps -x | grep bash
```


##2. Manage Virtual Terminals with Screen
###2 Create and navigate screens
```
screen
```
ctrl a c -> make a new screen  
ctrl a n->navigate to next screen  
ctrl a p->previous screen  
ctrl a->last used screen  
ctrl a (123) -> go to numbered screen
ctrl a shift "  ->show running screens  
ctrl a shift A ->name the current screen(must under current screen)  

###3 Detach and reattach screens
ctrl a d-> detach session(current screen)


####00:37
list screen
```
screen -ls
```
attach to the most recently used session
```
screen -R
```
attach using pid
```
screen -r 1234
```

####01:32 command mode.
in list mode( ctrl a shift :),  
ctrk b shift : ->command mode  


ctrl a k ->kill current window 
ctrl a \ ->kill all windows


##3. Manage Virtual Terminates with Tmux
###2 Create a session and work with windows
```
tmux
```
ctrl b ? ->shortcuts  
(q->quit)  
ctrl b c ->create window


####01:53
ctrl b , ->change window name  (this is not permanent)  
ctrl b number -> jump window  
ctrl b n->navigate to next window
ctrl b p->previous window
ctrl b l->last window
ctrl b & ->close current window  
ctrl b w ->list all windows


###3 Create and modify panes within windows
ctrl b " -> split top bottom
ctrl b o ->cycle active pane  
ctrl b % ->split left right  
ctrl b ->   -> cycle direction  
ctrl b ; ->last-used pane   //ctl b ctl o  
ctrl b ctrl ->  -> change size in small increment  
ctrl b ! ->promote a pane to full window  
ctrl b x ->close a pane


###4 Detach and reattach sessions
ctrl b d ->detach window  
in shell
```
tmux attach -t 0
```
to reattach.   


ctrl b $ -> rename session (max 8 char) this is perm. so we can connect using name
```
tmux attach -t newname
```

####01:46
ctrl b s ->choose session  

kill session
```
tmux kill-session -t newname
```
###5 The tmux command line
ctrl b  shift : -> go to commandline  (for example, new-window = ctrl b c) , switch-window -t 0 = changewindow  

set-option -g monitor-activity on


###6 Customize tmux

```
vim .tmux.conf
```
then edit
```
set-option -g all-rename off  //tells Tmux not to rename my windows after I set a name.
set -g status-bg cyan
```
