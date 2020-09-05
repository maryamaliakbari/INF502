## 1.Draw a diagram of the commits and branches in repository
```
(base) cmp3896:handson ma3367$ git branch
* master
  math
(base) cmp3896:handson ma3367$ git checkout master
Already on 'master'
(base) cmp3896:handson ma3367$ git checkout math
Switched to branch 'math'
(base) cmp3896:handson ma3367$ git log --decorate
commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:13:48 2019 -0700

    Adding some more knowledge to the function

commit 654b490a181dedf82dd6deda5f9848d6cca05918
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:12:14 2019 -0700

    Added a draft of A.py

commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:08:47 2019 -0700

     Creating all files (all empty)
## 2.Try git log --graph --all to see the commit tree. What do you see?
```
(base) cmp3896:handson ma3367$ git log --graph --all
* commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:15:28 2019 -0700
|
|     Making a small change here
|
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
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
###It shows all the latest commits to the branches.      
## 3.Use git diff BRANCH_NAME to view the differences from a branch and the current branch. Summarize the difference from master to the other branch.
```
(base) cmp3896:handson ma3367$ git diff math
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
 (base) cmp3896:handson ma3367$ git diff master
diff --git a/A.py b/A.py
index dc1e9bd..0afa98c 100644
--- a/A.py
+++ b/A.py
@@ -1,3 +1,11 @@
 #this is just an example, do not freak out
 def calculate_this(operator, num1, num2):
-   print 'my knowledge is limited'     
+   if operator == 'sum':
+      print num1 + num2
+      print 'That was easy buddy'
+   else:
+      if operator == 'subtraction':
+         print num1 - num2
+         print 'I could handle that...'
+      else:
+         print 'my knowledge is limited'
diff --git a/B.py b/B.py
index c63f94c..e69de29 100644
--- a/B.py
+++ b/B.py
@@ -1 +0,0 @@
-# Another file that will receive a line of code... at least.
###In the master branch, there is only one line code. 
When we use git diff to view the other branch, it will show the different line code from the master branch, such as the calculate operator code. 

## 4.Write a command sequence to merge the non-master branch into master
```
(base) cmp3896:handson ma3367$ git checkout master
(base) cmp3896:handson ma3367$ git merge math
Updating 18931d1..f197c7f 
Fast-forward
 A.py | 10 +++++++++-
 1 file changed, 9 insertions(+), 1 deletion(-)


## 5.Write a command (or sequence) to (i) create a new branch called math (from the master) and (ii) change to this branch
```
(base) cmp3896:handson ma3367$ git branch -d math
Deleted branch math (was aea1f5a)
(base) cmp3896:handson ma3367$ git branch math
(base) cmp3896:handson ma3367$ git checkout math

## 6.Edit B.py adding the following source code below the content you have there
```
(base) cmp3896:handson ma3367$ pico B.py
(base) cmp3896:handson ma3367$ cat B.py
# Another file that will receive a line of code... at least.
print 'I know math, look:'
print 2+2


## 7.Write a command (or sequence) to commit your changes
```
(base) cmp3896:handson ma3367$ git commit B.py -m "adding source code"

## 8.Change back to the master branch and change B.py adding the following source code (commit your change to master):
```
(base) cmp3896:handson ma3367$ git checkout master
(base) cmp3896:handson ma3367$ pico B.py
(base) cmp3896:handson ma3367$ cat B.py
# Another file that will receive a line of code... at least.
print 'I know math, look:'
print 2+2
print 'hello world!'
(base) cmp3896:handson ma3367$ git commit B.py -m "adding hello world"

## 9.Write a command sequence to merge the math branch into master and describe what happened
```
(base) cmp3896:handson ma3367$ git merge math
Auto-merging B.py
CONFLICT (content): Merge conflict in B.py
Automatic merge failed; fix conflicts and then commit the result.
###Merge conflict happens because we're trying to edit the same exact section on the file & git didn't aware which file to save.

## 10.Write a set of commands to abort the merge
```
(base) cmp3896:handson ma3367$ git merge --abort

## 11.Now repeat item 9, but proceed with the manual merge (Editing B.py). All implemented methods are needed. Explain your procedure
```
###To avoid conflict first i needed to abort the merge then I had to open the B.py in editor and remove two lines and then use add command and merge command in git. 
or we can Abort the merge and checkout to the math branch, Copy the two lines and switche to master branch. Edit B.py and paste the two lines there. 

## 12.Write a command (or set of commands) to proceed with the merge and make master branch up-to-date
```
(base) cmp3896:handson ma3367$ git add B.py
(base) cmp3896:handson ma3367$ git commit -m "delete two lines"
(base) cmp3896:handson ma3367$ merge math
Updating f197c7f..e6f90b4
Fast-forward
 .swp | Bin 0 -> 12288 bytes
 B.py |   5 +++++
 2 files changed, 5 insertions(+)
 create mode 100644 .swp



## part 2
what i did:
1. pressed "Fork", In the repository "igorsteinmacher / INF502-Fall2020".
2. In my repository" maryamaliakbari/INF502-Fall2020", copied the link.
3. opened the terminal and typed "git clone [copied link]"
4. entered the workspace.
5. set up a file named "Aliakbari_Maryam.md".
6. git add Aliakbari_Maryam.md.
7. git commit -m "add Aliakbari_Maryam.md""
8. git remote add upstream https://github.com/igorsteinmacher/INF502-Fall2020.git.
9. git push.
9. In my own repository clicked the "pull request".

I have been on the GitHub for a long time to find the corresponding instructions and encountered some difficulties. Since i started to do this part on Tuesday right after the class, you had not created students folder yet and i was alittle confused about how and where create my file.
In general, if I can use GitHub skillfully(it needs lots of practice), I believe it will be very helpful for my future programming.
