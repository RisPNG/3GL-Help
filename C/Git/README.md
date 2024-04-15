# Git
[Git](https://git-scm.com/downloads) is used to perform Git-related operations. How else am I supposed to explain it.

## Installation
[Website](https://git-scm.com/downloads).

## Demo
Check gurrent Git status:
```
git status
```

Show all branch:
```
git branch
```

Switch to branch
```
git switch “branch”
```

Show all files and folder currently in branch's 
```
git ls-tree --name-only repo-name
```

Add or remove additional/existing files to/from index:
```
git add "filename"
git rm "filename"
```

Set commit message and push:
```
git commit -m "message" & git push
```

Pull from main branch:
```
git pull origin repo-name
```
