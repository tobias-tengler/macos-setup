TODO: 
- Disable Apple Music Popup
- Set English as default keyboard language on lock screen
- Install React DevTools, Relay DevTools, uBlock Origin
- Disable dock bouncing `defaults write com.apple.dock no-bouncing -bool TRUE`

## Setup peripherals

- Download [Logi Options Plus](https://www.logitech.com/de-ch/software/logi-options-plus.html) (for Logitech Mouse)
  - Naviagte to "Point and Scroll" > "Scrollwheel" and set "Standard" scrolling:
  
  ![image](https://github.com/tobias-tengler/macos-setup/assets/45513122/063c022b-2884-48ed-bda2-eacf4704f304)

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

### Configuring for work (Azure DevOps)

- Generate SSH key (key files should end in `_work`)

```sh
ssh-keygen -t rsa-sha2-256 -C tobias.tengler@digitecgalaxus.ch

eval "$(ssh-agent -s)"

cat >> ~/.ssh/config << EOL
Host dev.azure.com
  HostName dev.azure.com
  User git
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_rsa_work
EOL

ssh-add ~/.ssh/id_rsa_work
```

- Add key in Azure DevOps

```sh
pbcopy < ~/.ssh/id_rsa_work.pub
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
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
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

## Setup NuGet authentication

Follow [this guide](https://github.com/microsoft/artifacts-credprovider?tab=readme-ov-file#installation-on-linux-and-mac).

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

- k6

  ```sh
  brew install k6
  ```
