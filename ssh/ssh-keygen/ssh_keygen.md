# ssh-keygen


## Generating a key

### ed25519 ssh key

```shell
ssh-keygen -t ed25519
```
- -C : The -C flag is used to add a comment to the SSH key, typically to identify the key's purpose or owner, such as an email address or a descriptive note.
```
ssh-keygen -t ed25519 -C "your_email@gmail.com"
```
- -f : The -f flag is used to specify the filename for the newly generated SSH key pair. This flag allows us to define both the directory and the name of the private key file, with the public key file automatically being saved with a .pub extension
```
ssh-keygen -t ed25519 -f ~/.ssh/my_custom_key
```
