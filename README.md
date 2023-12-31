# Yandex git course
1. Interesting
2. Simple

   Watch git config data
   ```
   git config --list
   ```
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
   or
   git diff HEAD~ HEAD
   ```
   Compare branches
   ```
   git diff <branch_name1> <branch_name2>
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
   or for another branch
   git push -u origin feature/merge-request
   ```
   For second and etc files in current branch
   ```
   git push
   ```
   Take changes from remote branch
   ```
   git pull
   ```
   If conflict
   ```
   git pull origin main --rebase
   ```
   pull = fetch + merge
   pull --rebase = fetch + rebase

   Pre pull request
   ```
   git checkout main # перешли в main
   git pull # подтянули новые изменения в main
   git checkout my-branch # вернулись в рабочую ветку my-branch
   git merge main # влили main в новую ветку my-branch
   git push -u origin my-branch # отправили ветку my-branch в удалённый репозиторий
   ```
   Branches view command
   ```
   git branch
   ```
   View all branches, including remotes branches
   ```
   $ git branch -a
   * main
     remotes/origin/HEAD
     remotes/origin/main
     remotes/origin/v1.0-stable
     remotes/origin/experimental
   ```
   To take a quick look at an upstream branch, check it out directly:
   ```
   git checkout origin/experimental
   ```
   To work on that branch, create a local tracking branch, which is done automatically by:
   ```
   git checkout experimental
   ```
   Create new branch
   ```
   git branch <branch_name>
   ```
   Rename branch
   ```
   git branch -M <new_branch_name>
   ```
   Branch moving (branch forcing). Move branch to old hash.
   ```
   git branch -f <branch_name> <hash>
   ``` 
   Switch to another branch
   ```
   git checkout <branch name>
   ```
   Create a branch and immediately switch to it
   ```
   git checkout -b <branch name>
   ```
   Detached HEAD, when HEAD link not to branch, but on the hash
   ```
   git checkout <hash>
   ```
   Restore file from old commit
   ```
   git checkout <hash> <file>
   ```
   Git cntrl+c
   ```
   git stash
   ```
   Git cntrl+v
   ```
   git stash pop
   ```
   Before starting the merge process, you need to go to the branch where the changes should be added. For exmaple if we want to merge feature/diff into main:
   ```
   git checkout main
   git merge feature/diff
   ```
   Delete branch after merge
   ```
   git branch -D feature/diff
   or
   git branch -d feature/diff
   ```
   1. The -d option is an alias for --delete, which only deletes the branch if it has already been fully merged in its upstream branch.
   2. The -D option is an alias for --delete --force, which deletes the branch "irrespective of its merged status."

   Copy commit from one branch to another (merge analog), may change commit message using --edit flag
   ```
   git cherry-pick <hash>
   or
   git cherry-pick <hash> --edit
   or
   git cherry-pick <hash> --no-commit
   ```
   Keeping Fork Up To Date
   1. Origin is a fork
   ```
   git remote -v
   origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
   origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
   ```
   2. Upstream is basic project
   ```
   git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
   ```
   3. Verify the new upstream repository
   ```
   git remote -v
   origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
   origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
   upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
   upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
   ```
   4. Synced fork with the upstream repository
   ```
   git pull upstream main
   ```
   Fast-forward state
   Две ветки находятся в состоянии fast-forward, если одну из них можно «перемотать» вперёд и она будет содержать те же коммиты, что и другая.
   ```bash
   $ git branch
   * add-docs
     main
   
   $ git log --oneline
   e08fa2a (HEAD -> add-docs) New docs 2
   fd588b2 New docs 1
   997d9ce (main) Commit 4
   0313e8e Commit 3
   5848aba Commit 2
   04923d7 Commit 1

   $ git checkout main
   
   $ git merge add-docs
   Updating 997d9ce..e08fa2a
   Fast-forward
    docs.txt | 1 +
    1 file changed, 1 insertion(+)
    create mode 100644 docs.txt
   
   $ git log --oneline
   e08fa2a (HEAD -> main, add-docs) New docs 2
   fd588b2 New docs 1
   997d9ce Commit 4
   0313e8e Commit 3
   5848aba Commit 2
   04923d7 Commit 1
   ```
   Disdable Fast-forward
   ```
   git merge --no-ff add-docs
   or
   git config [--global] merge.ff false
   ```
   If Fast-forward is disbled, merge will create merge commit
   ```bash
      # находимся в ветке main
   # --no-edit отключает ввод сообщения для merge-коммита
   # --no-ff отключает fast-forward слияние веток
   $ git merge --no-edit --no-ff add-docs
   Merge made by the 'ort' strategy.
    docs.txt | 1 +
    1 file changed, 1 insertion(+)
    create mode 100644 docs.txt
   
   # с флагом --graph
   # Git нарисует ветки с помощью «палочек» и «звёздочек»
   # получившийся коммит слияния: 6814789
   $ git log --graph --oneline
   *   6814789 (HEAD -> main) Merge branch 'add-docs'
   |\
   | * e08fa2a (add-docs) New docs 2
   | * fd588b2 New docs 1
   |/
   * 997d9ce Commit 4
   * 0313e8e Commit 3
   * 5848aba Commit 2
   * 04923d7 Commit 1
   ```
   Non-fast-forward state: the stories of two branches "diverge"
   ```bash
   # команде git log можно указать несколько веток,
   # и тогда она выведет их все
   $ git log --graph --oneline main add-docs
   * 15d3f04 (HEAD -> main) Commit 5
   | * 8de42eb (add-docs) New docs 2
   | * 4d3c346 New docs 1
   |/
   * 73def1e Commit 4
   * 9c30ab3 Commit 3
   * 83cc5ec Commit 2
   * 8e87fb2 Commit 1
   ```
   When merging non-fast-forward branches, Git creates a merge commit.
   ```bash
      # находимся в ветке main
   # --no-edit избавляет от необходимости
   # вводить сообщение для merge-коммита
   $ git merge --no-edit add-docs
   Merge made by the 'ort' strategy.
    docs.txt | 1 +
    1 file changed, 1 insertion(+)
    create mode 100644 docs.txt
   
   # коммит слияния: 34f5f8f
   $ git log --graph --oneline
   *   34f5f8f (HEAD -> main) Merge branch 'add-docs'
   |\
   | * 8de42eb (add-docs) New docs 2
   | * 4d3c346 New docs 1
   * | 15d3f04 Commit 5
   |/
   * 73def1e Commit 4
   * 9c30ab3 Commit 3
   * 83cc5ec Commit 2
   * 8e87fb2 Commit 1
   ```

