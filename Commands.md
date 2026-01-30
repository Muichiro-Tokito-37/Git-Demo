# Basic-Basic:
pwd (show current directory)
ls (list items) (we can also combine different flags like: ls -l + ls -a = ls -la)
cd (change directory)
cd ..  (or) cd ../../../ (to go back once or thrice, or whatever times in the directory)
clear (clear the screen)
exit (exit terminal)
mkdir <-folder name-> (make a new folder in the current directory)
touch <-file Name-> (it's use case is differen, read manual, but we can also use to create new files)

# git basic help:
git
git log
# git version check:
git --version
# configuring Git:
git config --global user.name  "My Name"
git config --global user.email  "Mymail@gmail.com"
git config --list
# cloing a repo in local Machine/Folder:
<!-- first, in the bash/terminal navigate to the offline folder where you want to clone the repo to -->
git clone <-some line->
# Show status of the code:
<!-- status: shows status of code (un-tracked, un-modified, modified, staged) -->
git status
<!--un-tracked means = git is not taking record of the file, the file is un-tracked by git. 
    un-tracked, means the file is not added to repo, once added, it become 'tracked' but un-modified or normal file 
    modified == edited the file,
    staged == file staged and is ready to be commited, after staging we commit changes and it becomes un-modified-->
<!-- for the above explained, below are the basic commands: -->
# Basic Commands (add, commit, push):
<!--add: adds new or changed files in your working directory to the Git staging area. -->
<!-- using 'add' makes the file transition from untracked/unmodified/modified to -> staged -->
git add <-file name-> (ex: git add index.html)
git add . (use this to upload ALL the files, so that you don't have to write names of each)

<!-- commit: it is the record of change -->
<!-- commit makes the file go from 'staged' to ->unmodified/normal -->
<!-- files still in local machine only, we can push once ready. -->
git commit -m "some message, adding a msg in compulsory"
git commit -am "somme msg" <!-- this adds + commits in the same line -->

<!-- push: upload local repo content to remote repo -->
<!-- using this will make all changes commited in local machine to reflect on the website/github/online repo -->
git push origin main
<!-- origin: the link 'https://www.github.com/muchiro......' or simply the address from where we took this file/repo -->
<!-- main: where to push -->

# creating new repo locally (init):
<!-- init: used to create a new git repo, locally, we will now have a .git folder in the same repo, which is where meta data of repo is stored. ENTER git init INSIDE THE FOLDER WHICH YOU WANT TO CONVERT INTO A NEW REPO -->
git init
git remote add <-remote-name-> <-remote-url->
<!-- git remote add origin <-link->, origin is the name given to the remote repo  -->
git remote -v           (to verify remote, simply:confirm the REPO where we are pull/fetch ing files from and push ing files to )
git branch              (to check branch)  
git branch -M main      (to rename branch)
git push origin main    (finally after creating the git repo online too, we can now push our code there.)
git push -m origin main (This means:“Push my local main branch to the main branch on the remote called origin.”)
                        (-u == --set-upstream)
                        (now we can simply write 'git push' or 'git pull' instead of 'git push origin main')
git commit -am "<-msg->" : used when we haven't added a new file, just modified the existing ones.

# Work Flow:

GITHUB  : code_changes --> commit 
LOCAL   : code_changes --> 'add' --> 'commit' --> 'push'
        add     == 'stage_a_change'
        commit  == 'commit_changes'

# Branch Commands:
git branch              (to check branch)
git branch -M main      (to rename branch) (-M and -m are a lil different)
git checkout <-b.name-> (to navigate)
git checkout -b <-new b.name->  (to create new branch)
git branch -d <-b.name->      (to delete branch)

<!-- then again in the new branch after making changes, add then commit, then push using:
git push origin feature
    this will push the new commit in feature branch, not main, we'll then merge this 2 branches later on
    you can also use 
git push -u origin feature 
    or
    if you are going to commit multiple times and want to use the short cut: 'git push' or 'git pull' -->

# Merging Code:
git diff <-branch name->        (to compare commits, branch, files & more.)
git merge <-branch name->       (to merge branches)
    or
Create PR

# basic (Pull) commands:
<!-- used to fetch and download content from a remote repo and immediately update the local repo to match that content -->
git pull origin main

# Fixing Mistakes:
<!-- 1. Staged changes -->
<!-- if you have staged/add a mistake but not done 'commit' yet, you can go one step back using: -->
git reset <-file name-> <!-- if want to reset changes of 1 file only>
git reset               <!-- if want to reset changes of all files>

<!-- 2. Commited changes (for one commit) -->
<!-- if you have commited a mistake you can go back 1 commit backwards using: -->
git reset HEAD~1

<!-- 3. Commited changes (for multiple commits) -->
<!-- if you have commited multiple mistakes changes, you can go back 'n' commits back using commit hash, every commit gets a hash value, they will pop in reverse chronological order(oldest/first commit is at the bottom, and latest commits are up in the list), which can be accessed using 'git log' -->
<!-- use the hash value of the commit where you want to go to -->
git reset <-commit hash->
<!-- if you don't want to see the later changes of after a certain commit and also go to that commit at the same time, use: -->
git reset --hard <-commit hash->

# Important command:
<!-- even after using 'git reset; to remove changes, from 'add' or 'commit', your local files will still show the changes in the local files, in order to go make those file in the last version where this changes weren't present use: -->
git restore <-file name->
    or
git restore <!-- to restore changes from all files >
