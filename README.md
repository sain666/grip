## Introduction

Grip stands for Git Reimplemented In Python, it is a project which implement a simple but functional subset of the version control system Git. 
It includes 10 shell scripts named `grip-init` `grip-add` `grip-commit` `grip-log` `grip-show` `grip-rm` `grip-status` `grip-branch` (`grip-checkout` `grip-merge`).

## description

- `grip-init` command creates an empty Grip repository.
- `grip-add` command adds the contents of one or more files to the index.
- `grip-commit [-a]` command saves a copy of all files in the index to the repository, if -a is used then all files already in the index to have their contents from the current directory added to the index before the commit.
- `grip-log` command prints a line for every commit made to the repository.
- `grip-show [commit]:filename` should print the contents of the specified filename as of the specified commit.
If commit is omitted, the contents of the file in the index should be printed.
- `grip-rm [--force] [--cached] filenames` removes a file from the index, or, from the current directory and the index.
If the --cached option is specified, the file is removed only from the index, and not from the current directory.
grip-rm, like git rm, should stop the user accidentally losing work, and should give an error message instead if the removal would cause the user to lose work. The --force option overrides this, and will carry out the removal even if the user will lose work.
- `grip-status` shows the status of files in the current directory, the index, and the repository.
- `grip-branch [-d] [branch-name]` either creates a branch, deletes a branch, or lists current branch names.

## Examples

**Subset0**
```
./grip-init
Initialized empty grip repository in .grip
echo line 1 > a
echo hello world >b
./grip-add a b
./grip-commit -m 'first commit'
Committed as commit 0
echo  line 2 >>a
./grip-add a
./grip-commit -m 'second commit'
Committed as commit 1
./grip-log
1 second commit
0 first commit
echo line 3 >>a
./grip-add a
echo line 4 >>a
./grip-show 0:a
line 1
./grip-show 1:a
line 1
line 2
./grip-show :a
line 1
line 2
line 3
cat a
line 1
line 2
line 3
line 4
./grip-show 0:b
hello world
./grip-show 1:b
hello world
```

**Subset1**
```
./grip-init
Initialized empty grip repository in .grip
touch a b c d e f g h
./grip-add a b c d e f
./grip-commit -m 'first commit'
Committed as commit 0
echo hello >a
echo hello >b
./grip-commit -a -m 'second commit'
Committed as commit 1
echo world >>a
echo world >>b
echo hello world >c
./grip-add a
echo world >>b
rm d
./grip-rm e
./grip-add g
./grip-status
a - file changed, changes staged for commit
b - file changed, changes not staged for commit
c - file changed, changes not staged for commit
d - file deleted
e - file deleted, deleted from index
f - same as repo
g - added to index
grip-add - untracked
grip-branch - untracked
grip-checkout - untracked
grip-commit - untracked
grip-init - untracked
grip-log - untracked
grip-merge - untracked
grip-rm - untracked
grip-show - untracked
grip-status - untracked
grip.py - untracked
h - untracked
```
**Mark**: 86.2/100 (High Distinction)

