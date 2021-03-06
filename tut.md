# Git: a distributed version control system  :smile:
	
## 1. basic operations
### 1.1 global configure
```bash
$ git config --global user.name "Your Name"  
$ git config --global user.email "email@example.com"  
```
### 1.2 establish a repository
```bash
$ mkdir learngit
$ cd learngit 
$ pwd  
$ git init  
$ ls -ah
```
### 1.3 commit file
+ can add many times and commit together
+ Git tracks and manages changes, not files
```bash
$ vi readme.txt  
$ cat readme.txt
$ git add readme.txt  
$ git commit -m "wrote a readme file"  
```
### 1.4 working directory & repository
![image](https://user-images.githubusercontent.com/68600731/143546204-74206219-5ec7-4609-b2f0-c206c307e9a6.png)	

### 1.5 check and back

+ HEAD represent the current version, that is, the latest commit; last version is `HEAD^`，and the previous one is `HEAD^^`; Of course 100 is too large, thus, `HEAD~100`.  
+ The fallback speed is very fast, because Git has an internal `HEAD` pointer
+ `HEAD` to current branch, branch to current version

![image](https://user-images.githubusercontent.com/68600731/143549858-52b4573a-0bea-4b60-8043-fd7a332ef670.png)

```bash
$ git status 
$ git diff readme.txt 
$ git diff HEAD -- readme.txt
	
$ git log        # commit history
$ git log --pretty=oneline
$ git log --graph
$ git log --abbrev-commit
	
$ git reset --hard HEAD^
$ git reset --hard <commit id>

$ git reflog     # command history
```
### 1.6 undo
```bash
# Return this file to the state when it was last `git commit` or `git add`.
$ git checkout -- readme.txt   

# unstage
$ git reset HEAD readme.txt
```
### 1.7 delete
```bash
$ rm readme.txt     # or manually
$ git rm readme.txt
$ git commit -m "remove readme.txt"

$ git checkout -- readme.txt   # delete file and regret
```
### 1.8 tag
Tags are linked to commits, not branches.
```bash
$ git tag <v1.0>
$ git tag <v0.9> <commit id>
$ git tag -a <v0.1> -m "version 0.1 released" <1094adb>

$ git tag
$ git show <tagname>

$ git push <origin> <v1.0>
$ git push <origin> --tags

$ git tag -d v0.9
$ git push <origin> :refs/tags/v0.9
```
### 1.9 DIY git
```bash
$ git config --global color.ui true

# alias, if global then configure file in user/.git/config
$ git config alias.<st> <status>
$ git config --global alias.<unstage> <reset HEAD>
```	
### 1.10 `.gitignore`
	$ git check-ignore -v App.class
	
	.*
	*.class
	!.gitignore        # not included
	!App.class

## 2. branch
### 2.1 create, switch, check, delete
```bash
$ git checkout -b <branch>    # create and switch
$ git switch -c <branch>      

$ git branch <branch>         # create

$ git checkout <branch>       # switch
$ git switch master      

$ git branch

$ git branch -d <branch>
$ git branch -D <branch>
```
### 2.2 merge
Solve conflict manually, if it exists.
```bash
	# Merge a branch into the current branch
	$ git merge <branch>   
```
![image](https://user-images.githubusercontent.com/68600731/143560774-72027609-4f92-4b7b-9f98-467fc4cf71cb.png)

```bash	
	# no fast forward, can see merge action in log.
	$ git merge --no-ff <branch>
	$ git merge --no-ff -m "merge with no-ff" <branch>
```
![image](https://user-images.githubusercontent.com/68600731/143560957-13bf8385-0711-4469-b964-5e33fde6ae09.png)

```bash	
	# Copy a specific commit to the current branch
	$ git cherry-pick <commit id>
```
	
### 2.3 stash
```bash
$ git stash
$ git stash list

$ git stash pop  # = apply + drop

$ git stash apply
$ git stash apply <stash@{0}>
$ git stash drop
```

## 3. Git remote :wink:

### 3.1 SSH
in user directory, then find content in id_rsa.pub 
```bash
$ ssh-keygen -t rsa -C "youremail@example.com"
```
### 3.2 remote repository
```bash
# one to all
$ git remote add <github> git@github.com:michaelliao/learngit.git
$ git remote add <gitee> git@gitee.com:liaoxuefeng/learngit.git

$ git push -u <origin> master    # first push
$ git push <origin> master

$ git checkout -b <dev> <origin/dev>
$ git push <origin> <dev>

$ git remote
$ git remote -v

$ git remote rm <origin>
```	
### 3.3 clone and pull	
```bash
$ git clone git@github.com:michaelliao/gitskills.git

$ git branch --set-upstream-to=<origin/dev> <dev>
$ git pull
```	
### 3.4 rebase ahuh I have no idea wtf
```bash
$ git rebase
```
