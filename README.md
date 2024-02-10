## Version Control System
A **Version Control System (VCS)** is a software tool that helps manage changes to source code over time. There are two primary types of version control systems: centralized and distributed.

#### **Centralized Version Control System (CVCS):**
In a centralized VCS, there is a single, central repository that stores all versions of the project files.
Developers check out files from this central repository to work on them locally.
Changes are made and then committed back to the central repository.
Examples of centralized VCS include *CVS (Concurrent Versions System)* and *Subversion (SVN)*.

#### **Distributed Version Control System (DVCS):**
In a distributed VCS, every developer has a complete copy (or clone) of the entire repository, including the entire project history.
Each developer can work independently, committing changes to their local repository.
Developers can also synchronize their changes with other repositories, typically by pushing and pulling changes between repositories.
Examples of distributed VCS include *Git* and *Mercurial*.

#### Difference between CVCS and DVCS:
The main difference between centralized and distributed version control systems lies in how they handle repositories and collaboration. In a centralized system, there's a single central repository, while in a distributed system, every developer has their own repository, and these repositories can be synchronized with one another. Distributed systems offer benefits like improved offline work capabilities, easier branching and merging, and greater resilience.



## Git - A Distributed Version Control System
Download and install the `git` from official website.Follow thw below tuorial to learn how to use git using command line tool 


### Checking `git` Version
To check the version of git installed on your system, you can use the following command in the terminal or command prompt:

```bash
git --version
```


### Setting up git configurations
To configure your git username and email globally, use the following commands:

```bash
git config --global user.name "user user"
git config --global user.email "user@gmail.com"
```
To verify that your git configurations have been set correctly, you can use the following command to list all configured settings:

```bash
git config --list
```


### Git help
To get help on a specific git command, you can use either of the following formats:

```bash
git help <verb>
git <verb> --help
```


### Initializing a git repository
To initialize a new git repository in your current directory, you can use the following command:

```bash
# move to project folder to be tracked 
cd local-repo/

# see list of files
ls -la

# initialize the repository
git init

# see list of files
ls -la
```

This command sets up a new git repository, creating a .git subdirectory where git stores its internal files and configuration for tracking changes in your project.


### Stop tracking a project
To stop tracking a project and remove the git repository from your directory, you can use the following command:

```bash
rm -rf .git
```

### Checking the status of the repository
To check the status of git repository, including information about modified, staged, and untracked files, use the following command:

```bash
git status
```


### Creating a .gitignore file
The `.gitignore` file serves as a powerful tool in git repositories by preventing unnecessary files from being tracked.

- Preventing unnecessary files from being tracked
- Maintaining security and privacy
- Maintaining Project Structure

To create a `.gitignore` file in your project directory, you can use the following command:

```bash
touch .gitignore
```

Inside `.gitignore` mention the files to be ignored
```.gitignore
.project
.vcxproj
```


### Adding files to staging area
The `git add` command adds a change in the working directory to the staging area, which later will be commited.

```bash
# adding a single file
git add filename.txt

# adding multiple Files
git add file1.txt file2.txt

# adding al modified files
git add .

# adding files matching a pattern
git add *.txt

```
Note:

- After executing git add, the specified files are staged, but changes are not yet committed to the repository. To permanently record these changes, they must be committed using git commit.


### Removing files from the staging area
To remove files from the staging area in git, you can use the `git reset` command.

```bash
# removing a single file 
git reset filename.txt

# remove all files from staging
git reset
```


### Performing a git commit
The `git commit` command is used to save changes to the repository. It records a snapshot of the changes staged in the staging area and creates a new commit containing these changes along with a commit message to describe the changes.

```bash
git commit -m "Commit message"
```

Commit message : <br>
Specifies a short, descriptive message summarizing the changes made in the commit. This message should be informative and concise, helping others understand the purpose of the commit.


### Viewing Commit History
The `git log` command is used to display the commit history of a repository.It presents a chronological list of commits, providing information such as the commit hash, author, date, and commit message for each commit.

```bash
git log
git log --stat
```


### Example workflow
1. Stage changes using `git add` to prepare them for committing.
2. Verify the changes staged for the commit using `git status`.
3. Commit the staged changes using `git commit -m "Commit message"`.
4. Review the commit history with `git log` to ensure the changes were committed as expected.


### Cloning a Remote Repository 
The `git clone` command is used to create a copy of a remote repository on your local machine.

```bash
git clone <repository_URL> <where to clone>
```

### Displaying Remote Repository URLs
The `git remote -v` command is used to display the URLs of remote repositories associated with your local repository. This command shows both the fetch and push URLs for each remote repository, allowing you to view where your local repository is configured to fetch from and push to.

```bash
git remote -v
```


### The universal diff Command
The `git diff` command is used to display the differences between the changes in your working directory and the staging area, or between the staging area and the latest commit (HEAD), or between any two commits, branches, or files in your repository.

To view the difference between the working directory and the staging area

```bash
git diff 
git diff <file_name>
```

To view the difference between the staging area and the latest commit (HEAD)

```bash
git diff --staged
git diff --staged <file_name>
git diff --cached <file_name>
```

To view the difference between two commits, branches, or files

```bash
git diff <branch_name1> <branch_name2> <file_name>
git diff <commit_hash> <commit_hash> <file_name>
```

### Git pull
The `git pull` command is used to fetch and integrate changes from a remote repository into the current branch of your local repository. It effectively combines two actions: `git fetch`, which retrieves changes from the remote repository, and `git merge`, which incorporates those changes into your current branch.

```bash
git pull <remote_name> <branch_name>
```
### Git push
The `git push` command is used to upload local repository content to a remote repository. It is commonly used to publish new commits made on a local branch to a remote repository, allowing collaboration with other developers and ensuring that changes are synchronized across multiple copies of the repository.

```bash
git push <remote_name> <branch_name>
```

### Creating a new branch
To create a new branch in git, you can use the `git branch` command followed by the name of the new branch you want to create. Optionally, you can specify the starting point (commit or branch) from which the new branch will be created.

```bash
git branch <new_branch_name> [<starting_point>]
```

Examples: 

Creating a New Branch from the Current Commit (HEAD)
```bash
git branch feature-branch
```

Creating a New Branch from a Specific Commit
```bash
git branch experimental-branch abc123
```

Creating a branch does not switch to the new branch automatically. You need to explicitly switch to the new branch if you want to start working on it immediately. Use `git checkout <branch_name>` or `git switch <branch_name>` to switch to the new branch 

```bash
git checkout <new_branch_name>
git switch <new_branch_name>
```


### Push local branch to remote
To push a local branch to a remote repository in git, you can use the git push command along with the name of the remote repository and the local branch you want to push.

```bash
git push -u <remote_name> <local_branch_name>
```

### Merge branches
The `git merge` command is used to integrate changes from one branch into another. It combines the changes from the specified branch (the source branch) into the current branch (the destination branch).

```bash
git merge <source_branch>
```
`<source_branch>`: Specifies the branch from which you want to merge changes into the current branch.

Note:
- Before using git merge, ensure that you are on the branch where you want to merge the changes (the destination branch).
- When you run git merge `<source_branch>`, git attempts to integrate the changes from the specified source branch into the current branch.
- If there are no conflicts between the changes in the source and destination branches, git will automatically merge the changes and create a new merge commit.
- If there are conflicts between the changes in the source and destination branches, git will pause the merge process and prompt you to resolve the conflicts manually. You can use tools like `git mergetool` or edit the conflicting files directly to resolve conflicts.
- After resolving conflicts, you need to commit the merge to finalize the process and create a new merge commit.

### Decluttering the repository
- Run `git branch --merged` to list branches that have been fully merged into the current branch.

```bash
git branch --merged
```

- Review the output to identify branches that can be safely deleted.
- Optionally, delete merged branches using `git branch -d <branch_name>` for local branches or `git push --delete <remote_name> <branch_name>` for remote branches.

```bash
git branch -d <branch_name>
git push --delete <remote_name> <branch_name>
```

### Git stash
The `git stash` command is used to temporarily store changes in your working directory that are not ready to be committed yet. It allows you to save your current changes and revert your working directory to a clean state, which can be useful when you need to switch branches or work on a different task without committing your changes.

```bash
git stash push -m "Stash message"
```

The `git stash list` command is used to display the list of stashed changes in your repository.

```bash
git stash list
```

The `git stash apply` command is used to apply the most recent stash (i.e., the stash at the top of the stash stack) to the working directory **while keeping the stash intact**.

When multiple stashes are present and want to apply a specific stash other than the most recent one, it can be specified by the stash index using `git stash apply stash@{<index>}`.

```bash
git stash apply
git stash apply stash@{<index>}
```

But `git stash pop`, which applies the most recent stash to the working directory and removes it from the stash stack.

```bash
git stash pop
```

The `git stash drop` command is used to remove stashed changes from the stash stack. It deletes the most recent stash by default, or one can specify a specific stash to drop by providing its index.

```bash
git stash drop
git stash drop stash@{<index>}
```

The `git stash clear` command is used to remove all stashed changes from the stash stack. It permanently deletes all stashed changes, and there is no way to recover them after using this command.

```bash
git stash clear
```
