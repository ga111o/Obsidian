## install zsh

```
sudo apt-get install zsh
```

<br>

![](https://velog.velcdn.com/images/ga111o/post/479905d8-d585-4ea3-91e5-82b255c0da90/image.png)

check shells.<br>
at bottom exist `/usr/bin/zsh`, successfully installed

<br>

change basic shell

```
chsh -s $(which zsh)
```

<small>`chsh`: change shell</small>

<hr>

## install oh-my-zsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
