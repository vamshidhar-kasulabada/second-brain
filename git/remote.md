# remote in git


## Check the remote url
```bash
git remote -v
```

## Changing the remote url
```bash
git remote set-url origin <new-remote-url>
```

- HTTPS:
```bash
git remote set-url origin https://github.com/username/repository.git
```

- SSH:
```bash
git remote set-url origin git@github.com:username/repository.git
```
