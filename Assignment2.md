## 1.Draw a diagram of the commits and branches in repository
```
(base) cmp3896:handson ma3367$ git branch
* master
(base) cmp3896:handson ma3367$ git checkout master
Already on 'master'

(base) cmp3896:handson ma3367$ git log --decorate
commit 9ad3766598b638931af8c1bb851b6538e46355f9 (HEAD -> master)
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 12:00:04 2020 -0700

    adding source code

commit b4ddf3b1dd5258adaf4ae4cb9f1ed57e43603ece
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 11:54:33 2020 -0700

    creating B.py to do assignments

commit 8b8ed6ece6b712f917670afb2422619d07be979b
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 11:35:34 2020 -0700

    creating A.py to do assignments
## 2.Try git log --graph --all to see the commit tree. What do you see?
```
(base) cmp3896:handson ma3367$ git log --graph --all
* commit 9ad3766598b638931af8c1bb851b6538e46355f9 (HEAD -> master)
| Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
| Date:   Thu Sep 3 12:00:04 2020 -0700
| 
|     adding source code
| 
* commit b4ddf3b1dd5258adaf4ae4cb9f1ed57e43603ece
| Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
| Date:   Thu Sep 3 11:54:33 2020 -0700
| 
|     creating B.py to do assignments
| 
* commit 8b8ed6ece6b712f917670afb2422619d07be979b
  Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
  Date:   Thu Sep 3 11:35:34 2020 -0700
  
      creating A.py to do assignments
## 3.Use git diff BRANCH_NAME to view the differences from a branch and the current branch. Summarize the difference from master to the other branch.
```
(base) cmp3896:handson ma3367$ git branch math
(base) cmp3896:handson ma3367$ git diff math
(base) cmp3896:handson ma3367$ log --graph --all
log: unrecognized option `--graph'
usage:
    log <command>

global options:
    -?, --help
    -q, --quiet
    -v, --verbose

commands:
    collect         gather system logs into a log archive
    config          view/change logging system settings
    erase           delete system logging data
    show            view/search system logs
    stream          watch live system logs
    stats           show system logging statistics

further help:
    log help <command>
    log help predicates
## 4.Write a command sequence to merge the non-master branch into master
```
(base) cmp3896:handson ma3367$ git checkout master
(base) cmp3896:handson ma3367$ git merge math

## 5.Write a command (or sequence) to (i) create a new branch called math (from the master) and (ii) change to this branch
```
(base) cmp3896:handson ma3367$ git branch math
(base) cmp3896:handson ma3367$ git diff math

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
(base) cmp3896:handson ma3367$ git log
commit 9ad3766598b638931af8c1bb851b6538e46355f9 (HEAD -> master)
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 12:00:04 2020 -0700

    adding source code

commit b4ddf3b1dd5258adaf4ae4cb9f1ed57e43603ece
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 11:54:33 2020 -0700

    creating B.py to do assignments

commit 8b8ed6ece6b712f917670afb2422619d07be979b
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 11:35:34 2020 -0700

    creating A.py to do assignments

(base) cmp3896:handson ma3367$ git show
commit 9ad3766598b638931af8c1bb851b6538e46355f9 (HEAD -> master)
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 12:00:04 2020 -0700

    adding source code

diff --git a/B.py b/B.py
index c63f94c..e6a2ded 100644
--- a/B.py
+++ b/B.py
@@ -1 +1,4 @@
 # Another file that will receive a line of code... at least.
+print 'I know math, look:'
+print 2+2
+
## 8.Change back to the master branch and change B.py adding the following source code (commit your change to master):
```
(base) cmp3896:handson ma3367$ git diff master
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
(base) cmp3896:handson ma3367$ git log
commit 9ad3766598b638931af8c1bb851b6538e46355f9 (HEAD -> math)
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 12:00:04 2020 -0700

    adding source code

commit b4ddf3b1dd5258adaf4ae4cb9f1ed57e43603ece
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 11:54:33 2020 -0700

    creating B.py to do assignments

commit 8b8ed6ece6b712f917670afb2422619d07be979b
Author: Maryam Aliakbari <ma3367@cmp3896.computers.nau.edu>
Date:   Thu Sep 3 11:35:34 2020 -0700

    creating A.py to do assignments
## 10.Write a set of commands to abort the merge
```
(base) cmp3896:handson ma3367$ git merge --abort

## 11.Now repeat item 9, but proceed with the manual merge (Editing B.py). All implemented methods are needed. Explain your procedure
```

## 12.Write a command (or set of commands) to proceed with the merge and make master branch up-to-date
```
