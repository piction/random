# random

## Git help

### Get nice logging

==> add 'lognice' as alias (~/.gitconfig)
```
[alias]
  lognice = log --graph  --decorate --format=format:'%C(yellow)%h%C(reset)%C(auto)%d%C(reset) %C(normal)%s%C(reset) %C(dim white)- %an%C(reset) %C(dim blue)(%ar)' --all
```


### Move existing tag to head
```
git push origin :refs/tags/<tagname>
git tag -fa <tagname>
git push origin master --tags
```


