### Ignore file
```
.DS_Store
```
### Ignore all files ended on .jpeg
```
*.jpeg
```
### Ignore all files "tmp" for all subfolders in docs folder
```
docs/*/tmp
```
### Ignore files (? - one symbol)
```
file?.txt
```
### Ignore file0.txt, file1.txt и file2.txt
```
file[0-2].txt
```
### Ignore todo.txt only in main folder.
### spam.txt will be ignore in folder and all subfolders
```
/todo.txt

spam.txt
```

### Ignore only folders, not files
```
build/
```
### Ignore files "docs/current/tmp", "docs/old/tmp", "docs/old/saved/a/b/c/d/tmp", "docs/tmp"
```
docs/**/tmp
```
### Except ignore
```
*.jpeg

!doge.jpeg
```
