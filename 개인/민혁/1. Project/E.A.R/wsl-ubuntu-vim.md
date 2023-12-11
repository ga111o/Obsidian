# How to Use vim


move file directory `cd {TREE}`

<br>

## vim basic command

`vim {FILE_NAME}`
<br>load file to vim

- `:q`: quit
- `:w`: save
- `:sq`: save and quit
- `:e {FILE_NAME}`:open file
- `q!`: kill
- `f`: file info



`i`: edit mode (*--insert--* mark at left bottom)<br>
- `esc`: view mode
- `h`: move left
- `l`: move right
- `j`: move bottom
- `k`: move top
- `ctrl + f`: next page
- `ctrl + b`: prev page
- `:{LINE_NUMBER}`: move that line
  <hr>
- `v`: set block (word)
- `shift + v`: set block (line)
- `ctrl + v`: set block (block)
  <hr>
- `y`: copy block
- `p`: paste copied block
  <hr>
- `x`: delete word
- `dd`: delete line
- <hr>
- `u`: undo
- `ctrl + r`: redo
