# HowTo: Transfer a git repo to azure devops

## Step 1

Close and remove the repo from all git clients/gui interfaces, like GitHub desktop.
Make sure you have a git command line client installed.

Navigate to the repo, and run `git config --local --edit`

Replace the file with (modify to suit your needs)
```
[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[submodule]
    active = .
[remote "origin"]
    url = https://USER@dev.azure.com/USER/PROJECT/_git/PROJECT
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
    remote = origin
    merge = refs/heads/main
[lfs]
    repositoryformatversion = 0
[lfs "https://dev.azure.com/USER/PROJECT/_git/PROJECT.git/info/lfs"]
    access = basic
[lfs "https://dev.azure.com/USER/PROJECT/_git/PROJECT/info/lfs/objects/"]
    access = basic
```

## Step 2

Attempt to push(or pull) from the repo - You'll be required to enter a username and password.
Your username is that of your microsoft account's,

The PAT can be found at
`https://dev.azure.com/USER/_git/PROJECT` when you press on the `clone` button in the top right, and press `generate git credentials`
Otherwise, press in the top right on the `user settings` button, click on `personal access tokens` and make sure the following is set 
![image](https://github.com/MyDragonBreath/MyDragonBreath/assets/38029594/39d1a44f-a4c6-4c06-9161-99db191b3964)

SSH tokens can also be generated from the `user settings` menu, which wont require re-entering the PAT

Once a push or pull works,

### Step 2 B

run `git lfs init` if LFS is required

### Step 2 C

Re add the repos to your client/gui of choice
