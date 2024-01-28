- Download [Logi Options Plus](https://www.logitech.com/de-ch/software/logi-options-plus.html) (for Logitech Mouse)
  - Naviagte to "Point and Scroll" > "Scrollwheel" and set "Standard" scrolling:
  
  ![image](https://github.com/tobias-tengler/macos-setup/assets/45513122/063c022b-2884-48ed-bda2-eacf4704f304)

- Generate SSH Key [Reference](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

```sh
ssh-keygen -t ed25519 -C 45513122+tobias-tengler@users.noreply.github.com

eval "$(ssh-agent -s)"

cat > ~/.ssh/config << EOL
Host github.com
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519
EOL

ssh-add ~/.ssh/id_ed25519
```

- Add key to [GitHub](https://github.com/settings/keys) [Reference](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)


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

- Install Nerd Font

```sh
p10k configure
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
- [Setup shell dot-files](https://github.com/tobias-tengler/shell-config)
