1. List all the branches in this repository and, for each branch, list the commits.

    - Use `git branch` to list the branches in this repository.
    - Use `git checkout` to explore each branch.
    - Use `git log --decorate` to explore the structure of commits.

```
ram@Jawahars-MacBook-Pro handson % git branch
* master
  math
ram@Jawahars-MacBook-Pro handson % git commit
On branch master
nothing to commit, working tree clean
ram@Jawahars-MacBook-Pro handson % git checkout         
ram@Jawahars-MacBook-Pro handson % git commit  
On branch master
nothing to commit, working tree clean
ram@Jawahars-MacBook-Pro handson % git checkout master  
Already on 'master'
ram@Jawahars-MacBook-Pro handson % git commit         
On branch master
nothing to commit, working tree clean
ram@Jawahars-MacBook-Pro handson % git log --decorate   
commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (HEAD -> master)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:15:28 2019 -0700

    Making a small change here

commit 654b490a181dedf82dd6deda5f9848d6cca05918
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:12:14 2019 -0700

    Added a draft of A.py

commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:08:47 2019 -0700

     Creating all files (all empty)
ram@Jawahars-MacBook-Pro handson % git commit
On branch master
nothing to commit, working tree clean

```

2. Try `git log --graph --all` to see the commit tree. Paste the result here and write a paragraph to provide an interpretation of what you found.
```
ram@Jawahars-MacBook-Pro handson % git log --graph --all
* commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (HEAD -> master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:15:28 2019 -0700
| 
|     Making a small change here
|   
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (math)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:13:48 2019 -0700
|   
|       Adding some more knowledge to the function
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700
  
       Creating all files (all empty)
       
A visual representation of how a developer's multiple development pipelines have branched and merged over time is produced by the git log graph command. In this case, git log —graph —all is used to show all the branches. The head master branch is the first to be shown, and changes were made there before more math knowledge was added to the function. Then, after creating all of the files, the draft of A.py was inserted.

```

3. Use `git diff BRANCH_NAME` to view the differences from a branch and the current branch. Summarize the difference from master to the other branch.

```
ram@Jawahars-MacBook-Pro handson % git diff math       
diff --git a/A.py b/A.py
index 0afa98c..dc1e9bd 100644
--- a/A.py
+++ b/A.py
@@ -1,11 +1,3 @@
 #this is just an example, do not freak out
 def calculate_this(operator, num1, num2):
-   if operator == 'sum':
-      print num1 + num2
-      print 'That was easy buddy'
-   else:
-      if operator == 'subtraction':
-         print num1 - num2
-         print 'I could handle that...'
-      else:
-         print 'my knowledge is limited'
+   print 'my knowledge is limited'     
diff --git a/B.py b/B.py
index e69de29..c63f94c 100644
--- a/B.py
+++ b/B.py
@@ -0,0 +1 @@
+# Another file that will receive a line of code... at least.

When a Git repository is first established, a branch will automatically be created. The master branch is the default branch. A Git repository allows for the creation of numerous additional branches. The branch that has code in production is called master. In due course, all development code is merged into master. A variety of supporting branches are used during the development cycle, and then they are all merged into the master.

```

4. Write a command sequence to merge the non-master branch into `master`.

```
git checkout master
git merge math

```


5. Write a command (or sequence) to (i) create a new branch called `math` (from the `master`) and (ii) change to this branch.

```
git checkout master
git branch math (fatal: a branch named 'math' already exists)
git checkout math

```
   
6. Edit B.py adding the following source code below the content you have there.
```
ram@Jawahars-MacBook-Pro handson % git add B.py        
ram@Jawahars-MacBook-Pro handson % git status          
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   B.py

ram@Jawahars-MacBook-Pro handson % git commit -m "B.py"
[master b5ce381] B.py
 1 file changed, 2 insertions(+), 2 deletions(-)
```

7. Write a command (or sequence) to commit your changes.
```
git add B.py
git commit -m "addition of two lines to B.py on math branch"

```

8. Change back to the `master` branch and change B.py adding the following source code (commit your change to `master`):
```
print 'hello world!'

git checkout master
git add B.py
git commit -m "adding one line to B.py on master branch"

```

9. Write a command sequence to merge the `math` branch into `master` and describe what happened.
```
ram@Jawahars-MacBook-Pro handson % git merge math
Already up to date. 

git checkout master 
git merge math

```
   
10. Write a set of commands to abort the merge.
```
git merge --abort

```
   
11. Now repeat item 9, but proceed with the manual merge (editing B.py). All implemented methods are needed. Explain your procedure.
```
No errors are seen. None of the files are copied

```

12. Write a command (or set of commands) to proceed with the merge and make `master` branch up-to-date.
```
git checkout master
git merge math
git rebase

```

13. Complete Part 2. Then, come back here and answer the following:
Report your experience of submitting the Part 2. Please, include the steps you followed, the commands you used, and the hurdles you faced (within the file you created for the **Part 1**).
```
First it was difficult for me to fnd where should I need to create the .md for part2.
After finding it and adding all the details of the recent paper which I have gone through. Again I struggeld to find how to perform pull request. And finally some how I did the pull request and sharing my experience of the part 2. But it was a great oppurtunity for me to learn about the Git. 

Thank you ANA..

```
