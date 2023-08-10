macos zsh prompt add git branch
===============================



`vi .zshrc`

```
#!/bin/zsh

# show git branch
#export PROMPT="%n@%m %1~ %# "
git-branch() {
  git symbolic-ref --short -q HEAD 2> /dev/null
}
git-prompt() {
  local branch=`git-branch`
  if [ $branch ]; then printf "(%s)" $branch; fi
}
setopt prompt_subst
export PROMPT="%n@%m %1~ \$(git-prompt)%# "
```



ps: bash

`vi .bash_profile`

```
#!/bin/bash

# show git branch
git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
export PS1="[\u@\h \W]\$(git_branch)\$ "
```



