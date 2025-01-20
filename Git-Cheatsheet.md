# Git Cheatsheet

Sugguested config:
```
git config --global core.editor nano
git config --global user.email "..."
git config --global user.name "..."
git config --global pull.ff only
git config --global alias.sl "log --format=oneline --graph -n15"
git config --global alias.sla "log --format=oneline --graph -n15 --all"
git config --global alias.sll "log --format=oneline --graph"
git config --global alias.ss "status -s"
git config --global alias.dd "difftool --tool=vimdiff3"
git config --global --add difftool.prompt false
git config --global log.abbrevcommit yes
git config --global core.abbrev 8
```
With the above config,

| Command   | Comment                                                                             |
| --------- | ----------------------------------------------------------------------------------- |
| `git sl`  | Show the most recent 15 history items, in compact form, including branch/merge info |
| `git sla` | Show the most recent 15 history items in compact form, all branches                 |
| `git sll` | Show all history in compact form, including branch/merge info                       |
| `git ss`  | Show status in short form                                                           |
| `git dd`  | Show diff using vimdiff3                                                            |

Change management commands:
| Command                                | Comment                                                                                                                                                                                                                 |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `git diff --staged`                    | Show diff of staged files (without `--staged`, it shows diff of modified but not staged files)                                                                                                                          |
| `git commit -a -m <msg>`               | Equivalent to `git add .` then `git commit -m <msg>`                                                                                                                                                                    |
| `git rm --cached <file>`               | Remove from staging area but keep the file (without `--cached` the file is also deleted)                                                                                                                                |
| `git mv <old> <new>`                   | Rename/move files in git                                                                                                                                                                                                |
| `git commit --amend`                   | Update the previous commit                                                                                                                                                                                              |
| `git restore --staged <file>`          | Unstage a file                                                                                                                                                                                                          |
| `git restore <file>`                   | Overwrite modified file using repo version (WARNING: will lose all edits)                                                                                                                                               |
| `git reset <commithash> [file]`        | Move HEAD to the given commit, update staging area, but don't touch working dir. <br> <commithash> can be `HEAD~`, `HEAD~2` etc. to denote the n-th ancestor of current HEAD. <br> Used to remove commits from history. |
| `git reset --hard <commithash> [file]` | Above, plus updating working dir (can cause data loss)                                                                                                                                                                  |
| `git reset --hard HEAD`                | Overwrite working dir from HEAD                                                                                                                                                                                         |

Remote repo and tags:
| Command                                  | Comment                                                                       |
| ---------------------------------------- | ----------------------------------------------------------------------------- |
| `git remote -v`                          | Show remote repo info                                                         |
| `git remote add <shortname> <url>`       | Add another remote repo                                                       |
| `git remote set-url origin <url>`        | Change remote repo                                                            |
| `git fetch <remote>`                     | Fetch from specific remote (doesn't touch workspace)                          |
| `git pull <remote> <branch>`             | Pull from specific remote repo and branch                                     |
| `git pull --rebase`                      | In case there are changes in both remote and local, perform rebase to resolve |
| `git tag`                                | List all tags                                                                 |
| `git tag -l <pattern>`                   | Show tags that match the pattern                                              |
| `git show <tagname>`                     | Show info of tag including commits                                            |
| `git tag -a <tagname> <commit hash>`     | Add tag after the fact at arbitrary commit                                    |
| `git push --tags`                        | Push to remote repo including tags (by default tags are not pushed)           |
| `git tag -d <tagname>`                   | Delete a tag                                                                  |
| `git push --delete <tagname>`            | Push the tag deletion to remote repo (by default not pushed)                  |
| `git checkout <tagname>`                 | Check out to the tag. Don't make changes because it's in unattached state     |
| `git checkout -b <branchname> <tagname>` | Create a branch based on the given tag. OK to make changes in the branch.     |
| `git checkout -`                         | Check out the head of main                                                    |

History:
| Command                                             | Comment                                                              |
| --------------------------------------------------- | -------------------------------------------------------------------- |
| `git log [--since=yyyy-mm-dd] [--until=yyyy-mm-dd]` | Show commits for specific date range                                 |
| `git log -S <text>`                                 | Show commits that change the number of occurrences of the given text |
| `git log -- <path>`                                 | Show commits that modify the given path                              |
| `git log --author <name>`                           | Show commits from specific author                                    |
| `git log --grep <text>`                             | Show commits with comment containing the given text                  |
| `git log --stats`                                   | Show statistics in commit history                                    |
| `git log -p -<n>`                                   | Show most recent n commits, with content diff                        |
| `git log <branchname>`                              | Show history from specific branch                                    |

Branches:
| Command                                        | Comment                                                                                                                                                                                                                                                |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `git branch -vv`                               | Show all branches, including how local branches track remote branches                                                                                                                                                                                  |
| `git branch --merged`                          | Show all branches that have been merged                                                                                                                                                                                                                |
| `git branch --no-merged`                       | Show all branches that have not been merged                                                                                                                                                                                                            |
| `git branch <bname>`                           | Create a local branch and not switch to it                                                                                                                                                                                                             |
| `git checkout <bname>`                         | Switch to the branch. If the local branch with the name doesn't exist,<br> but a remote branch of the name exists, then create local branch tracking <br> the remote branch then switch to it (equivalent to `git checkout -b <bname> orgion/<bname>`) |
| `git checkout -b <bname>`                      | Equivalent to `git branch <bname>` then `git checkout <bname>`                                                                                                                                                                                         |
| `git branch -d <bname>`                        | Delete a branch                                                                                                                                                                                                                                        |
| `git checkout -b <bname> origin/<remotebname>` | Create a local tracking branch based off the remote branch                                                                                                                                                                                             |
| `git checkout --track origin/<bname>`          | Same as above (use remote branch name as local branch name)                                                                                                                                                                                            |
| `git push --set-upstream origin <bname>`       | Create remote branch, make the current local branch track the newly created remote branch, and push                                                                                                                                                    |
| `git push origin --delete <bname>`             | Delete the remote branch                                                                                                                                                                                                                               |
| `git merge <bname>`                            | Merge the given branch into the current branch                                                                                                                                                                                                         |
| `git rebase <bname>`                           | Rebase the current branch to the given branch                                                                                                                                                                                                          |
| `git mergetool`                                | Run 3-way merge tool to perform merging (useful when there is merge conflict)                                                                                                                                                                          |
