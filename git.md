 # Lesson 1 

 Initializing git project:
```sh
$ git init
```

Three parts of git workflow:
 - Working Directory
 - Staging Area
 - Repository

Checking status of changes:
```sh
$ git status
```
Adding files to staging area:
```sh
$ git add filename
```
Checking the differences between the working directory and the staging area:
```sh
$ git diff filename
```

Storing changes from the staging area inside the repository:
```sh
$ git commit -m "commit message"
```
 Standard Conventions for Commit Messages:
+ Must be in quotation marks
+ Written in the present tense
+ Should be brief (50 characters or less) when using _-m_

Viewing commits stored chronologically in the repository:
```sh
$ git log
```

# Lesson 2

Viewing head commit (the commit you are currently on, mostly the most recent commit):
```sh
$ git show HEAD
```
Restoring the file in working directory from the last commit:
```sh
$ git checkout HEAD filename
```
Adding multiple files into the staging area in one command:
```sh
$ git add filename_1 filename_2
```
Unstaging files from the staging area
```sh
$ git reset HEAD filename
```
Rewinding to previous commit:
```sh
$ git reset (the first 7 characters of the SHA)
```




