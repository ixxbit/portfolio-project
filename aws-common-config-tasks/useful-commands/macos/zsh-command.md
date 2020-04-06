# Oh My Zsh Cheat Sheet

## What's this Oh My Zsh? <a id="whatsthisohmyzsh"></a>

Let's start with what Oh My Zsh is. Being a big fan of the Command Line Interface, I really hate using my computer mouse! This gave me a great motivation to search for awesome tools to enhance my User Experience on the Command Line. I came across [Oh-My-Zsh](https://go.praveen.science/?redirect=https://ohmyz.sh/) during a hackathon I attended back in 2014. A friend of mine convinced me to use this shell because of its simplicity and adjustability. Also, the CLI is hackable and extendable with many plugins.

## Contents <a id="contents"></a>

1. [What's this Oh My Zsh?]()
2. [Capabilities]()
3. [Installation]() 
   1. [Using cURL]()
   2. [Using wget]()
4. [Commands]()
5. [Aliases]() 
   1. [Alias Example]()
6. [Tab-completion]()
7. [Git]()
8. [Editors]()
9. [Symfony2]()
10. [tmux]()
11. [Systemd]() 
    1. [systemctl]()
12. [Upgrade]()

## Capabilities <a id="capabilities"></a>

This is a list of its capabilities:

* Command validation
* Spelling correction
* Sharing of command history among all running shells
* Command Line Themes \(Agnoster, RobbyRussell, etc.\)
* Directory history
* Startup / shutdown scripts via `zshenv`, `zprofile`, `zshrc`, `zlogin`, and `zlogout`
* Strong autocomplete capabilities. You can use the TAB key to navigate through the different options and use enter to select the right folder. Bash for example would print all the options. This is fairly spammy and pollutes your scrollback.
* Add plugins: e.g. Git plugin with a huge list of useful Git aliases.
* Display of active branch and visual feedback about your Git status:
  * Green: branch if no changes occurred
  * Yellow with a circle icon: untracked files
  * Yellow with a plus icon: files ready to be committed

## Installation <a id="installation"></a>

This article isn't about the installation, so please refer to its [original website](https://go.praveen.science/?redirect=https://ohmyz.sh/) for detailed installation guidance:.

Quick installation information is below here anyway:

### Using cURL <a id="usingcurl"></a>

```text
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"  
```

### Using wget <a id="usingwget"></a>

```text
$ sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

## Commands <a id="commands"></a>

| Command | Description |
| :--- | :--- |
| `tabs` | Create a new tab in the current directory \(macOS - requires enabling access for assistive devices under System Preferences\). |
| `take` | Create a new directory and change to it, will create intermediate directories as required. |
| `x` / `extract` | Extract an archive \(supported types: tar.{bz2,gz,xz,lzma}, bz2, rar, gz, tar, tbz2, tgz, zip, Z, 7z\). |
| `zsh_stats` | Get a list of the top 20 commands and how many times they have been run. |
| `uninstall_oh_my_zsh` | Uninstall Oh-my-zsh. |
| `upgrade_oh_my_zsh` | Upgrade Oh-my-zsh. |
| `source ~/.zshrc` | Uptake new changes |

## Aliases <a id="aliases"></a>

| Alias | Command |
| :--- | :--- |
| `alias` | list all aliases |
| `..` | `cd ..` |
| `...` | `cd ../..` |
| `....` | `cd ../../..` |
| `.....` | `cd ../../../..` |
| `/` | `cd /` |
| `~` | `cd ~` |
| `cd +n` | switch to directory number `n` |
| `1` | `cd -` |
| `2` | `cd -2` |
| `3` | `cd -3` |
| `4` | `cd -4` |
| `5` | `cd -5` |
| `6` | `cd -6` |
| `7` | `cd -7` |
| `8` | `cd -8` |
| `9` | `cd -9` |
| `md` | `mkdir -p` |
| `rd` | `rmdir` |
| `d` | `dirs -v` \(lists last used directories\) |

See `~/.oh-my-zsh/lib/directories.zsh`

### Alias Example <a id="aliasexample"></a>

```text
alias -s rb=vim #opens ruby files in vim  
# $ foo.rb 
# vim => foo.rb
alias -g gp='| grep -i' #creates a global alias for grep  
# $ ps ax gp ruby
# (all ruby process will be displayed)
```

| Flag | Description |
| :--- | :--- |
| `L` | print each alias in the form of calls to alias |
| `g` | list or define global aliases |
| `m` | print aliases matching specified pattern |
| `r` | list or define regular aliases |
| `s` | list or define suffix aliases |

## Tab-completion <a id="tabcompletion"></a>

| For options and helpful text of what they do |
| :--- |
| `ls -(tab)` |
| `cap (tab)` |
| `rake (tab)` |
| `ssh (tab)` |
| `sudo umount (tab)` |
| `kill (tab)` |
| `unrar (tab)` |

## Git <a id="git"></a>

| Dynamic access to current branch name with the current\_branch function |
| :--- |
| `git pull origin $(current_branch)` |
| `grb publish $(current_branch) origin` |

| Alias | Command |
| :--- | :--- |
| `g` | `git` |
| `ga` | `git add` |
| `gaa` | `git add --all` |
| `gapa` | `git add --patch` |
| `gb` | `git branch` |
| `gba` | `git branch -a` |
| `gbd` | `git branch -d` |
| `gbl` | `git blame -b -w` |
| `gbnm` | `git branch --no-merged` |
| `gbr` | `git branch --remote` |
| `gbs` | `git bisect` |
| `gbsb` | `git bisect bad` |
| `gbsg` | `git bisect good` |
| `gbsr` | `git bisect reset` |
| `gbss` | `git bisect start` |
| `gc` | `git commit -v` |
| `gc!` | `git commit -v --amend` |
| `gca` | `git commit -v -a` |
| `gca!` | `git commit -v -a --amend` |
| `gcan!` | `git commit -v -a --no-edit --amend` |
| `gcans!` | `git commit -v -a -s --no-edit --amend` |
| `gcam` | `git commit -a -m` |
| `gcsm` | `git commit -s -m` |
| `gcb` | `git checkout -b` |
| `gcf` | `git config --list` |
| `gcl` | `git clone --recursive` |
| `gclean` | `git clean -fd` |
| `gpristine` | `git reset --hard && git clean -dfx` |
| `gcm` | `git checkout master` |
| `gcd` | `git checkout develop` |
| `gcmsg` | `git commit -m` |
| `gco` | `git checkout` |
| `gcount` | `git shortlog -sn` |
| `gcp` | `git cherry-pick` |
| `gcpa` | `git cherry-pick --abort` |
| `gcpc` | `git cherry-pick --continue` |
| `gcs` | `git commit -S` |
| `gd` | `git diff` |
| `gdca` | `git diff --cached` |
| `gdct` | `git describe --tags &#96;git rev-list --tags --max-count=1&#96;` |
| `gdt` | `git diff-tree --no-commit-id --name-only -r` |
| `gdw` | `git diff --word-diff` |
| `gf` | `git fetch` |
| `gfa` | `git fetch --all --prune` |
| `gfo` | `git fetch origin` |
| `gg` | `git gui citool` |
| `gga` | `git gui citool --amend` |
| `ggpnp` | `git pull origin $(current_branch) && git push origin $(current_branch)` |
| `ggpull` | `git pull origin $(current_branch)` |
| `ggl` | `git pull origin $(current_branch)` |
| `ggpur` | `git pull --rebase origin $(current_branch)` |
| `glum` | `git pull upstream master` |
| `ggpush` | `git push origin $(current_branch)` |
| `ggp` | `git push origin $(current_branch)` |
| `ggfl` | `git push --force-with-lease origin <your_argument>/$(current_branch)` |
| `ggsup` | `git branch --set-upstream-to=origin/$(current_branch)` |
| `gpsup` | `git push --set-upstream origin $(current_branch)` |
| `gignore` | `git update-index --assume-unchanged` |
| `gignored` | `git ls-files -v &#124; grep "^\[\[:lower:\]\]"` |
| `git-svn-dcommit-push` | `git svn dcommit && git push github master:svntrunk` |
| `gk` | `gitk --all --branches` |
| `gl` | `git pull` |
| `glg` | `git log --stat --max-count = 10` |
| `glgg` | `git log --graph --max-count = 10` |
| `glgga` | `git log --graph --decorate --all` |
| `glo` | `git log --oneline --decorate --color` |
| `glog` | `git log --oneline --decorate --color --graph` |
| `glp` | `git_log_prettily (git log --pretty=$1)` |
| `gm` | `git merge` |
| `gmt` | `git mergetool --no-prompt` |
| `gp` | `git push` |
| `gpoat` | `git push origin --all && git push origin --tags` |
| `gr` | `git remote` |
| `grba` | `git rebase --abort` |
| `grbc` | `git rebase --continue` |
| `grbs` | `git rebase --skip` |
| `grbi` | `git rebase -i` |
| `grh` | `git reset HEAD` |
| `grhh` | `git reset HEAD --hard` |
| `grmv` | `git remote rename` |
| `grrm` | `git remote remove` |
| `grset` | `git remote set-url` |
| `grt` | `cd $(git rev-parse --show-toplevel &#124;&#124; echo ".")` |
| `grup` | `git remote update` |
| `grv` | `git remote -v` |
| `gsd` | `git svn dcommit` |
| `gsps` | `git show --pretty = short --show-signature` |
| `gsr` | `git svn rebase` |
| `gss` | `git status -s` |
| `gst` | `git status` |
| `gsta` | `git stash save` |
| `gstaa` | `git stash apply` |
| `gstd` | `git stash drop` |
| `gstl` | `git stash list` |
| `gstp` | `git stash pop` |
| `gsts` | `git stash show --text` |
| `gsu` | `git submodule update` |
| `gts` | `git tag -s` |
| `gunignore` | `git update-index --no-assume-unchanged` |
| `gunwip` | `git log -n 1 &#124; grep -q -c "\-\-wip\-\-" && git reset HEAD~1` |
| `gup` | `git pull --rebase` |
| `gvt` | `git verify-tag` |
| `gwch` | `git whatchanged -p --abbrev-commit --pretty = medium` |
| `gwip` | `git add -A; git ls-files --deleted -z &#124; xargs -r0 git rm; git commit -m "--wip--"` |

You also find these commands in Dash as a Cheat-sheet.

## Editors <a id="editors"></a>

| Alias | Command |
| :--- | :--- |
| `stt` | \(When using `sublime` plugin\) Open current directory in Sublime Text 2/3 |
| `v` | \(When using `vi-mode` plugin\) Edit current command line in Vim |

## Symfony2 <a id="symfony2"></a>

| Alias | Command |
| :--- | :--- |
| `sf` | `php ./app/console` |
| `sfcl` | `php app/console cache:clear` |
| `sfcontainer` | `sf debug:container` |
| `sfcw` | `sf cache:warmup` |
| `sfgb` | `sf generate:bundle` |
| `sfroute` | `sf debug:router` |
| `sfsr` | `sf server:run -vvv` |

## tmux <a id="tmux"></a>

| Alias | Command |
| :--- | :--- |
| `ta` | `tmux attach -t` |
| `tad` | `tmux attach -d -t` |
| `ts` | `tmux new-session -s` |
| `tl` | `tmux list-sessions` |
| `tksv` | `tmux kill-server` |
| `tkss` | `tmux kill-session -t` |

## Systemd <a id="systemd"></a>

### systemctl <a id="systemctl"></a>

| Command | Description |
| :--- | :--- |
| `sc-status NAME` | show the status of the NAME process |
| `sc-show NAME` | show the NAME systemd `.service` file |
| `sc-start NAME` | start the NAME process |
| `sc-stop NAME` | stop the NAME process |
| `sc-restart NAME` | restart the NAME process |
| `sc-enable NAME` | enable the NAME process to start at boot |
| `sc-disable NAME` | disable the NAME process at boot |

## Upgrade <a id="upgrade"></a>

To upgrade .oh-my-zsh, run:

```text
upgrade_oh_my_zsh  
```

