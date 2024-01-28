## Setup peripherals

- Download [Logi Options Plus](https://www.logitech.com/de-ch/software/logi-options-plus.html) (for Logitech Mouse)
  - Naviagte to "Point and Scroll" > "Scrollwheel" and set "Standard" scrolling:
  
  ![image](https://github.com/tobias-tengler/macos-setup/assets/45513122/063c022b-2884-48ed-bda2-eacf4704f304)

## Configure MacOS

- Settings > Keyboard > Keyboard Shortcuts > Function Keys: Enable "Use ... as standard function keys"
- Settings > Keyboard > Keyboard Shortcuts > Mission Control: Uncheck "Show Desktop (F11)"
- Settings > Trackpad: Enable "Tap to click"

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
```

- Add key in [GitHub settings](https://github.com/settings/keys) ([Reference](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account))

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

### Configuring for work (Azure DevOps)

- Create and import a new SSH key as outlined above and postfix the file with (`_work`)

- Configure Azure DevOps as a SSH host

```sh
cat >> ~/.ssh/config << EOL
Host dev.azure.com
	HostName dev.azure.com
	User git
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519_work
EOL
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

## Shell setup

Follow [this guide](https://github.com/tobias-tengler/shell-config)

## Terminal setup

1. Open iTerm2 settings
2. Navigate to "Profiles" > "Other actions" > "Import profile from JSON"
3. Import `~/.config/shell/iterm2-profile.json`

## Neovim setup

Follow [this guide](https://github.com/tobias-tengler/neovim-config)
