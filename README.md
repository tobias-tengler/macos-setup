- Generate SSH Key

```sh
ssh-keygen -t ed25519 -C 45513122+tobias-tengler@users.noreply.github.com

eval "$(ssh-agent -s)"

# TODO: Update config file

ssh-add ~/.ssh/id_ed25519
```

- Add key to [GitHub](https://github.com/settings/keys)

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

- Download [Chrome](https://www.google.com/chrome/)
- Install [homebrew](https://brew.sh/)

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

- Install [iTerm2](https://iterm2.com/)

```sh
brew install --cask iterm2
```

- Install [oh-my-zsh](https://ohmyz.sh/)

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- Install [Powerlevel10k Theme](https://github.com/romkatv/powerlevel10k)

```sh
git clone --depth=1 git@github.com:romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

- Install oh-my-zsh plugins
  - [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

  ```sh
  git clone git@github.com:zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM}/plugins/zsh-autosuggestions
  ```
  
  - [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
  ```sh
  git clone git@github.com:zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM}/plugins/zsh-syntax-highlighting
  ```
- Setup shell config; TODO Link Github
