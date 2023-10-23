

#### Restart terminal without closing on MacOS
```
exec zsh -l
```

```
cat ~/.zshrc
```

```
gitpush() {
    git add .
    git commit -m "Workbench workspace sync"
    git push
}
alias gp=gitpush
alias gs="git status -su"
```

```
git config --global user.name
```

```
git config --global user.email
```

https://stackoverflow.com/questions/7773181/git-keeps-prompting-me-for-a-password
