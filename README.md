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
  - Paste at `bash_profile`:
  ```
  if [ -f $(brew --prefix)/etc/bash_completion ]; then
    . $(brew --prefix)/etc/bash_completion
  fi
  ```
  - Save `~/.bash_profile`
- Run source `~/.bash_profile`
- Now when you press `tab` on a git command, it will auto complete.
