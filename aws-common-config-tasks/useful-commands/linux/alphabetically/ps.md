# ps

### `fyi:`

#### stuck \[output\]

There is usually no correlation between a _stuck_ process of `top` and a non-responding application:

* _stuck_ means that the process is currently un-interruptible which usually is the case if the process is waiting for a disk or network data block to be read \(or similar low-level stuff\). Technically speaking the process is executing in kernel space \(aka Unix kernel\) and can not be interrupted \(so even a `kill -9` wouldn't have any impact\). Usually these _stuck_ states only last milliseconds \(as you can see in `top` as well because the number of _stuck_ processes changes with every display cycle\).
* _non-responding applications_ can be _too_ busy to reply to any event OS X throws at them.

I see one situation where a _stuck_ process corresponds to a non-responding application: A process can be _stuck_ for a very long time, perhaps stuck endlessly, without any possibility to kill it. This usually is the result of some programming error, e.g. improper disconnection from a networked device then the kernel keeps trying to read from it. In cases like this even a forced termination will not remove the process.  


_ref:_ [_https://apple.stackexchange.com/questions/58697/how-does-stuck-in-results-of-top-relate-to-not-responding-in-activity-m/58718\#58718_](https://apple.stackexchange.com/questions/58697/how-does-stuck-in-results-of-top-relate-to-not-responding-in-activity-m/58718#58718)\_\_

`-------`

\`\`

`-----`

## ps... 

`ps aux` or you could sort the list of process when you open top, for example: Sort by memory usage: `top -o rsize` Sort by CPU usage: `top -o cpu` It's not exactly the whole list



----------  
if you are using ps, you can check the manual

```text
man ps
```

there is a list of keywords allowing you to build what you need. for example to show, userid / processid / percent cpu / percent memory / work queue / command :

```text
ps -e -o "uid pid pcpu pmem wq comm"
```

-e is similar to -A \(all inclusive; your processes and others\), and -o is to force a format. 

if you are looking for a specific uid, you can chain it using awk or grep such as :

```text
ps -e -o "uid pid pcpu pmem wq comm" | grep 501
```

this should \(almost\) show only for userid 501. try it.  




### `ps -aux`

list all processes running from all users, -ux will list only processes of current user

\`\`

