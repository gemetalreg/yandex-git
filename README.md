# Yandex git course
1. Interesting
2. Simple

   Create git project
   ```
   git init
   ```
   
   Files in project have 4 status: untracked, tracked, staged, modified.
   ```mermaid
   graph LR;
   untracked -- "git add <file>" --> staged;
   staged    -- "git commit -m <message>" --> tracked/comitted;
   ```
   
   After first commit
   ```mermaid
   graph LR;
   modified/tracked -- "git add <file>" --> staged;
   staged    -- "git commit -m <message>" --> tracked/comitted;
   ```
   To see differences between commit and modified
   ```
   git diff
   ```
   To see differences between commit and staged
   ```
   git diff --staged
   ```
   To see differnces betwen commit1 and commit2
   ```
   git diff <commit1> <commit2>
   ```

   Watch files status
   ```
   git status
   ```

   Add changes to git
   ```
   git add --all
   ```

   Commit changes in project
   ```
   git commit -m "Some changes"
   ```
   Addding staging changes to last commit
   ```
   git commit --amend --no-edit
   git commit --amend -m "<new message>"
   ```
   
   Git revert changes in modified file in working directory
   ```
   git restore <file>
   ```

   Git revert changes in file in staged
   ```
   git restore --staged <file>
   ```

   Git reset to old commit, unchangeable
   ```
   git reset --hard <commit hash>
   ```

   Git log show information about commits: their hashes, Author, date and message.
   ```
   git log
   ```
   Also, there's short version of git log
   ```
   git log --oneline
   ```

   Head is a file, that link to last commit.

   Remote add github repository named by origin
   ```
   git remote add origin <repository-link>
   ```
   Make sure the repositories are linked
   ```
   $ git remote -v
   origin    git@github.com:yandex-praktikum/git-clone-lesson.git (fetch)
   origin    git@github.com:yandex-praktikum/git-clone-lesson.git (push)
   ```
   Create a copy of the remote repository on your computer
   ```
   git clone <https://github.com/yandex-praktikum/git-clone-lesson>
   ```
   Make upstream for pushing git changes for first time
   ```
   git push -u origin main
   ```

   For second and etc
   ```
   git push
   ```
   Braches view command
   ```
   git branch
   ```
   Create new branch
   ```
   git branch <branch_name>
   ```
   
