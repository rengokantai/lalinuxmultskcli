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
