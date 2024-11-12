# config


The configuration file in the SSH directory, usually located at ~/.ssh/config, is used to simplify and manage SSH connections. It allows you to set various SSH connection options on a per-host basis or globally. Here are some key purposes of the ~/.ssh/config file:



## Host

Host is simply a convenient label that we can use to refer to a specific set of SSH connection settings. We can choose any name we like for these aliases, as long as we remember to use to correclty.

## HostName

The HostName specifies the actual domain name or IP address of the server we are connecting to.

## IdentityFile

IdentityFile is the path to the private key file used for authenticating an SSH connection``


## config file for setuping multiple github accounts
```
# Personal Github account
Host personal-github
    HostName github.com
    user git
    IdentityFile ~/.ssh/id_rsa_personal


# Work Github account
Host work-github
    HostName github.com
    user git
    IdentityFile ~/.ssh/id_rsa_work
```
