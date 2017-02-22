# git Configs
------------------
Choose which step do you want, and roll until there:

### 1. Auto Completing
### 2. Terminal Color and Branch Indication
### 3. Exluding Unecessary Files from Remote
### 4. Generating a SSH key
-----------------------
#### 1. Auto Completing
- First [installs Homebrew](https://brew.sh/), a package manage for macOS.
- Second opens terminal (`cmd + space` and write `terminal`):
  - On Terminal run `brew install bash-completion`
  - Open `~/.bash_profile`
    - You can type `nano ~/.bash_profile` to open
    - If you doesn't have `nano`, install by `brew install nano`
  - Paste the come below at `bash_profile`:
  ```
  if [ -f $(brew --prefix)/etc/bash_completion ]; then
    . $(brew --prefix)/etc/bash_completion
  fi
  ```
  - Save `~/.bash_profile`
- Run `source ~/.bash_profile` on terminal.
- Now when you press `tab` on a git command, it will auto complete.
-----------------------
#### 2. Terminal Color and Branch Indication
- Open `~/.bash_profile`
  - You can type `nano ~/.bash_profile` to open
  - If you doesn't have `nano`, install by `brew install nano`
- Paste at the end of `bash_profile`:
```
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
```
This "function" will get the branch that you are working.
- Now to change the Prompt String One (PS1), the string before each command
on terminal, we have some different designs.
- Choose which PS1 do you want based on the pictures below, and copy the code
related to the picture.
  1. Design 1
  ```
  export PS1="\u@\h \[\033[32m\] | \w\[\033[33m\] | \$(parse_git_branch)\[\033[00m\] \n $ "
  ```
  ![img1] (https://github.com/lhcavalcanti/git_configs_osx/blob/master/images/%231.png?raw=true)
    ```
    User @ Computer | path until actual folder | branch
    $ :
    ```
  2. Design 2
  ```
    export PS1="\u@\h \[\033[32m\] | \W\[\033[33m\] | \$(parse_git_branch)\[\033[00m\] \n $ "
  ```
  ![img2] (https://github.com/lhcavalcanti/git_configs_osx/blob/master/images/%232.png?raw=true)
    ```
    User @ Computer | actual folder | branch
    $ :
    ```
  3. Design 3
  ```
    export PS1="\u@\h \[\033[32m\] | \w\[\033[33m\] | \$(parse_git_branch)\[\033[00m\] $ "
  ```
  ![img3] (https://github.com/lhcavalcanti/git_configs_osx/blob/master/images/%233.png?raw=true)
    ```
    User @ Computer | path until actual folder | branch $ :
    ```
