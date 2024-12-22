# HOMEBREW

Homebrew is a popular package manager for macOS and Linux that simplifies the process of installing, managing, and updating software. This documentation provides an overview of the most common commands and workflows in Homebrew.

## HomeBrew Installation(Apple Sillicon)

### Step 1: Install Xcode Command Line Tools
Homebrew requires the Xcode Command Line Tools, which can be installed with this command:
```bash
xcode-select --install
```
A popup will appear. Click Install and wait for the installation to complete.


### Step 2: Install Homebrew
Run the following command to install Homebrew:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
This script automatically detects the M1 architecture and installs Homebrew in `/opt/homebrew` (default for M1).

### Step 3: Add Homebrew to PATH
After installation, follow the on-screen instructions to add Homebrew to your shell’s PATH. Usually, you need to add this line to your shell configuration file:

For zsh (default on macOS):
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
eval "$(/opt/homebrew/bin/brew shellenv)"
```

For bash:
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.bash_profile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### Step 4: Verify Installation
Ensure that Homebrew is installed and accessible by runniung:
```bash
brew --version
```
The output should display the installeld version of Homebrew

### Step 5: Install Packages
You can now install packages unsing Homebrew. For Example:
```bash
brew install git
```
### Step 6: Troubleshooting

If you encounter issues:

- Run `brew doctor` to diagnose problems.
- Ensure your shell configuration file is correctly updated with the `brew shellenv` line.
