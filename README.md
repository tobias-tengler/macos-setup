TODO: 
- Disable Apple Music Popup
- Set English as default keyboard language on lock screen
- Install React DevTools, Relay DevTools, uBlock Origin
- Disable dock bouncing `defaults write com.apple.dock no-bouncing -bool TRUE`

## Configure MacOS

- Settings > Dock > Show suggest and recent items: Disable
- Settings > Keyboard > Delay until Repeat: Short
- Settings > Keyboard > Key repeat rate: Fast
- Settings > Keyboard > Keyboard Shortcuts > Function Keys: Enable "Use ... as standard function keys"
- Settings > Keyboard > Keyboard Shortcuts > Mission Control: Uncheck "Show Desktop (F11)"
- Settings > Keyboard > Text Input > "Input Sources" + Edit >
  - Disable "Correct spelling automatically"
  - Disable "Capitalize words automatically"
  - Disable "Add period with double space"
- Settings > Trackpad: Enable "Tap to click"
- Configure holding down keys:

```sh
defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false
```

## Install basic software

- Install [homebrew](https://brew.sh/)

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

- Install [Chrome](https://www.google.com/chrome/)

```sh
brew install --cask google-chrome
```

- Install [VS Code](https://code.visualstudio.com/)

```sh
brew install --cask visual-studio-code
```

- Install git

  ```sh
  brew install git
  ```

- Install [iTerm2](https://iterm2.com/)

```sh
brew install --cask iterm2
```

- Install Docker ([Rancher Desktop](https://rancherdesktop.io))

## Install software SDKs

- Install [Rust](https://www.rust-lang.org/tools/install)

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

- Install [.NET](https://dotnet.microsoft.com/en-us/download#macos)

```sh
brew install --cask dotnet-sdk
```

```sh
sudo dotnet workload update
```

- Install Node.js ([nvm](https://github.com/nvm-sh/nvm))

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

```sh
# Important for the shell to have the relevant path
omz reload

cat > "$NVM_DIR/default-packages" << EOL
yarn
EOL
```

```sh
nvm install --lts

corepack enable
```

## Setup SSH

- Generate SSH Key ([Reference](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent))

```sh
ssh-keygen -t ed25519 -C 45513122+tobias-tengler@users.noreply.github.com

eval "$(ssh-agent -s)"

cat > ~/.ssh/config << EOL
Host github.com
  HostName github.com
  User git
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519
EOL

ssh-add ~/.ssh/id_ed25519

git config --global user.signingkey ~/.ssh/id_ed25519.pub
```

- Add key in [GitHub settings](https://github.com/settings/keys) both as authentication and signing key ([Reference](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account))

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

## Shell setup

Follow [this guide](https://github.com/tobias-tengler/shell-config)

## Terminal setup

1. Open iTerm2 settings
2. Navigate to "Profiles" > "Other actions" > "Import profile from JSON"
3. Import `~/.config/shell/iterm2-profile.json`

## Neovim setup

Follow [this guide](https://github.com/tobias-tengler/neovim-config)

## Additional software

- Redis

  ```sh
  brew install redis
  ```

- Watchman

  ```sh
  brew install watchman
  ```

- k9s

  ```sh
  brew install k9s
  ```

## Setup NuGet authentication

Follow [this guide](https://github.com/microsoft/artifacts-credprovider?tab=readme-ov-file#installation-on-linux-and-mac).
