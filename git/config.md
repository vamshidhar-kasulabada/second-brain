# git config
The git config command is used to set configuration options for Git. These configurations control aspects of Git's behavior, such as user information, editor preferences, and alias definitions. It can be applied at different levels to customize settings for a repository, a user, or the entire system.

Usage:
```bash
git config [options] [key] [value]
```


## Levels of Configuration

Git settings can be applied at three levels:

### System Level (`--system`)

Configuration is stored in the system-wide configuration file, affecting all users on the machine.

File:`/etc/gitconfig` or `/opt/homebrew/etc/gitconfig` in case of git is insatlled via homebrew
```bash
git config --system <key> <value>
```

### Global Level (`--global`)
Configuration is specific to a user. It applies to all repositories the user works on.

File: `~/.gitconfig` or `~/.config/git/config` 
```bash
git config --global <key> <value>
```

### Local Level (Default)
Configuration is specific to a single Git repository.

File: `.git/config` (inside the repository)
```bash
git config <key> <value>
```

Note: Settings at the local level override global and system-level settings.

## Setting values using config command

### Setting git username
```
git config --global user.name "vamshidhar kasulabada"
```
- `--systgem` set the user name for all repos for all the users on the sytem.
- `--global` sets the user name for all repos of the user currently logged in
- Default(no option specified) sets the user name for current repo
> Note: Use doublequotes while specifing a values for a key. value may contain spaces so using doublequotes is preferd. doublequotes can be omited when the value does not include a spaces within it.

## Getting values using config command
Usage:
```bash
git config [options] [key]
```
- When only a key is specified without a value then the value will be outputted
```bash
git config --global user.name
```
- Outputs the user name of the global user

Output:
```bash
vamshidhar-kasulabada
```

### Using `--get` flag

```bash
git config --get user.name
```
- gets the username of the working repo

Output:
```bash
vamshidhar-kasulabada
```

