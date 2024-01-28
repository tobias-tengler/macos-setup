## Setup peripherals

- Download [Logi Options Plus](https://www.logitech.com/de-ch/software/logi-options-plus.html) (for Logitech Mouse)
  - Naviagte to "Point and Scroll" > "Scrollwheel" and set "Standard" scrolling:
  
  ![image](https://github.com/tobias-tengler/macos-setup/assets/45513122/063c022b-2884-48ed-bda2-eacf4704f304)

## Configure MacOS

- Settings > Keyboard > Keyboard Shortcuts > Function Keys: Enable "Use ... as standard function keys"
- Settings > Keyboard > Keyboard Shortcuts > Mission Control: Uncheck "Show Desktop (F11)"
- Settings > Trackpad: Enable "Tap to click"

## Setup SSH

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

## Install basic software

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

## Shell setup

Follow [this guide](https://github.com/tobias-tengler/shell-config)
