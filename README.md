## Introduction

Grip stands for Git Reimplemented In Python, it is a project which implement a simple but functional subset of the version control system Git. 
It includes 10 shell scripts named `grip-init` `grip-add` `grip-commit` `grip-log` `grip-show` `grip-rm` `grip-status` `grip-branch` (`grip-checkout` `grip-merge`).

## description

The `grip-init` command creates an empty Grip repository.
The `grip-add` command adds the contents of one or more files to the index.
The `grip-commit [-a]` command saves a copy of all files in the index to the repository, if -a is used then all files already in the index to have their contents from the current directory added to the index before the commit.

The `grip-log` command prints a line for every commit made to the repository.
The `grip-show [commit]:filename` should print the contents of the specified filename as of the specified commit.
If commit is omitted, the contents of the file in the index should be printed.

The `grip-rm [--force] [--cached] filenames` removes a file from the index, or, from the current directory and the index.
If the --cached option is specified, the file is removed only from the index, and not from the current directory.
grip-rm, like git rm, should stop the user accidentally losing work, and should give an error message instead if the removal would cause the user to lose work.
The --force option overrides this, and will carry out the removal even if the user will lose work.

The `grip-status` shows the status of files in the current directory, the index, and the repository.
The `grip-branch [-d] [branch-name]` either creates a branch, deletes a branch, or lists current branch names.

- **Mark**: 86.1/100 (High Distinction)

