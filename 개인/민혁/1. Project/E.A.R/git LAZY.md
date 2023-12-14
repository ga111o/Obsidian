## Lazy git

git add, commit, push<br>
-> just one line

```
function lgit() {
    git add .
    git commit -a -m "$1"
    git push
}
```

```
lazygit "My commit msg"
```

type this at git terminal

[link](https://stackoverflow.com/questions/19595067/git-add-commit-and-push-commands-in-one)
