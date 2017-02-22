# Tutorial git Configs OSX
------------------
Choose which step do you want, and roll until there:

### 1. Auto Completing
### 2. Terminal Color and Branch Indication
### 3. Changing git output colors

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
  - Save and close `~/.bash_profile`
- Run `source ~/.bash_profile` on terminal.
- Now when you press `tab` on a git command, it will auto complete.

-----------------------
#### 2. Terminal Color and Branch Indication
- Open terminal (`cmd + space` and write `terminal`):
  - Open the file `~/.bash_profile`
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
  related to the picture you want.
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
    - Paste after the function `parse_git_branch`.
    - Save and close `~/.bash_profile`
  - Run `source ~/.bash_profile` on terminal.

If you use Linux please check this [link] (https://www.leaseweb.com/labs/2013/08/git-tip-show-your-branch-name-on-the-linux-prompt/) 

I suggest combine the commands on PS1 to fit your necessities, to understand
all commands there and learn other check this [link] (https://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html).


-----------------
#### 3. Changing git output colors
Although this tutorial focus on macOS users, this step also works on Linux!

- Open terminal (`cmd + space` and write `terminal`):
  - Run git command: `git config --global -e`
    - If you want to change your git editor run:
     `git config --global core.editor "editor"`
    - On "editor" put your preferable editor.
  - Paste the code below on it:
  ```
    [color]
        branch = auto
        diff = auto
        status = auto
            ui = true
    [color "branch"]
        current = yellow reverse
        local = yellow
        remote = green
    [color "diff"]
        meta = yellow bold
        frag = magenta bold
        old = red bold
        new = green bold
    [color "status"]
        added = yellow
        changed = green
        untracked = cyan
    ```
    As you can see this files setup the colors on git commands: branch, diff
    and status. You can search others commands or change the colors.

------------

I hope that you enjoy it! Any suggestion feel free to open a issue!

Thanks [@lhcavalcanti] (www.twitter.com/lhcavalcanti)
