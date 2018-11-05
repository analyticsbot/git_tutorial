<a href="http://analyticsbot.tk/wp-content/uploads/2018/11/download.png"><img class="alignnone size-full wp-image-1133" src="http://analyticsbot.tk/wp-content/uploads/2018/11/download.png" alt="" width="160" height="160" /></a>

[This is also available at <a href="http://analyticsbot.tk/2018/11/brief-tutorial-on-git-and-version-control-system/"> my blog</a>

In my <a href="http://analyticsbot.tk/2018/10/add-ssh-keys-to-github-bitbucket-on-windows/">last post</a>, I talked about how to setup SSH keys for github/ bitbucket. In this post, I will talk about some commonly used git commands, but first let's talk about the git workflow for a file.

<a href="http://analyticsbot.tk/wp-content/uploads/2018/11/git-flow.png"><img class="size-medium wp-image-1134 aligncenter" src="http://analyticsbot.tk/wp-content/uploads/2018/11/git-flow-300x57.png" alt="" width="300" height="57" /></a>

The local copy of the repository is on the machine where we code, the next is to index and stage the files, where the changes are staged before being pushed to the remote server. Some terms to remember:
<ul>
 	<li>local - this is the machine on which you are working</li>
 	<li>staging server - this is also on the local machine on which you are working and is one stage before the final push</li>
 	<li>remote - this is a remote server or a company server such as Github or Bitbucket</li>
 	<li>origin - origin is just a keyword that points to the remote server url. the remote repo is almost always called origin, but it doesn't have to be.</li>
 	<li>master - the name of the default branch that git creates for you when first creating a repo. In most cases, "master" means "the main branch", other branches can be created as well</li>
 	<li>branch - branch in Git is simply a lightweight movable pointer to one of these commits. A branch is used when a user wants to work on specific portion of the code without committing to master</li>
 	<li>head - the current commit your repo is on. Most of the time HEAD points to the latest commit in your current branch, but that doesn't have to be the case. HEAD really just means "what is my repo currently pointing at".</li>
</ul>
&nbsp;
<ul>
 	<li>git pull - this command is used to pull the changes from the remote repository. this sometimes might require an authentication (if the repo is not public or if you do not have access to it)</li>
</ul>
<pre class="lang:default decode:true">neo $git pull
Already up to date.
neo $
</pre>
<ul>
 	<li>git clone - this command is used to clone or copy a remote repository to the local for the first time. this sometimes might require an authentication (if the repo is not public or if you do not have access to it)</li>
</ul>
<pre class="lang:default decode:true">git clone ssh://john@example.com/path/to/my-project.git
cd my-project
# Start working on the project

# cloning a branch
git clone -branch new_feature git://remoterepository.git
</pre>
<ul>
 	<li>git add . - this command is used to index the files that have been changed/ added. Git only adds only new or removed lines.</li>
</ul>
<pre class="lang:default decode:true ">neo $git add .
neo $</pre>
<ul>
 	<li>git commit -m "message" - Once the files are indexed, the next step is to send the files to the staging area using commit. This is accompanied with a message that should convey the addition/ changes to the codebase.</li>
</ul>
<pre class="lang:default decode:true ">neo $git commit -m "added new ipynb files"
[master 7d8e453] added new ipynb files
 4 files changed, 5369 insertions(+)
 create mode 100644 coursera_deep_learning/Neural Networks and Deep Learning/Emojify+-+v2.ipynb
 create mode 100644 coursera_deep_learning/Neural Networks and Deep Learning/Neural+machine+translation+with+attention+-+v4.ipynb
 create mode 100644 coursera_deep_learning/Neural Networks and Deep Learning/Operations+on+word+vectors+-+v2.ipynb
 create mode 100644 coursera_deep_learning/Neural Networks and Deep Learning/Trigger+word+detection+-+v1.ipynb
neo $

</pre>
<ul>
 	<li>git push origin master - Once the files are staged, it still is only on the local server and has to be pushed to the remote server. the code is checked for any conflicts (such as more than one developer working on the same person of the code) and if not conflict is found, the pushed code is merged with the existing code on master</li>
</ul>
<pre class="lang:default decode:true">neo $git push origin master
Counting objects: 8, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (8/8), done.
Writing objects: 100% (8/8), 10.78 MiB | 528.00 KiB/s, done.
Total 8 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/analyticsbot/deep-learning.git
   5d0fd09..7d8e453  master -&gt; master
neo $</pre>
&nbsp;
<ul>
 	<li>git fetch - this command retrieves the code from the remote master to local staging, but the changes are not reflected locally, yet.</li>
</ul>
<pre class="lang:default decode:true ">neo $git fetch</pre>
<ul>
 	<li>git merge - this command is used along with ```git fetch``` and merges the remote with local</li>
</ul>
<pre class="lang:default decode:true ">neo $git merge
Already up to date.
neo $</pre>
<ul>
 	<li>git log - this command gives the log for the commits done from the local machine</li>
</ul>
<pre class="lang:default decode:true ">neo $git log
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code
:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

commit 79f69959e30b99a95ae1274488337c7814034498
:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

commit 79f69959e30b99a95ae1274488337c7814034498
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

commit 79f69959e30b99a95ae1274488337c7814034498
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 3 23:59:52 2018 -0700
:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

commit 79f69959e30b99a95ae1274488337c7814034498
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 3 23:59:52 2018 -0700

:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

commit 79f69959e30b99a95ae1274488337c7814034498
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 3 23:59:52 2018 -0700

    cnn course
:...skipping...
commit 7d8e45347a8308a301eb225c50a2ad00985caac1 (HEAD -&gt; master, origin/master, origin/HEAD)
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Nov 5 00:32:48 2018 -0800

    added new ipynb files

commit 5d0fd09fda7e2c501994142c5f84c8e617dda2b3
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 24 13:31:28 2018 -0700

    new files

commit 5400b60d5e667663bad9265ddbf9a69e23f4e3df
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:21:23 2018 -0700

    new courses

commit 95864955e0d7316fb8f7996707deb60b29519fa2
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Mon Oct 22 12:19:25 2018 -0700

    added code

commit 79f69959e30b99a95ae1274488337c7814034498
Author: ravi &lt;ravi.shankar1788@gmail.com&gt;
Date:   Wed Oct 3 23:59:52 2018 -0700

    cnn course
</pre>
The above command can also be used with a special parameter ```--oneline``` to avoid getting such a long output.
<pre class="lang:default decode:true ">neo $git log --oneline
7d8e453 (HEAD -&gt; master, origin/master, origin/HEAD) added new ipynb files
5d0fd09 new files
5400b60 new courses
9586495 added code
79f6995 cnn course
0f92184 Keras Happy House Notebook
279a194 dl course
1cc5aaf Experiment with MNIST using KERAS
7a05d80 :confetti_ball: Added .gitattributes &amp; .gitignore files
neo $
</pre>
<ul>
 	<li>git branch -- this command is used to create a new branch or to get an idea which is the current working branch against which changes will be pushed</li>
</ul>
<pre class="lang:default decode:true">neo $git branch
* master
  neo
neo $

neo $git branch neo</pre>
<ul>
 	<li>git checkout -- this command is used to shift to a specific branch, which should already exist</li>
</ul>
<pre class="lang:default decode:true">neo $git checkout neo
Switched to branch 'neo'
neo $

# create a new branch and switch to it
neo $git checkout -b new_branch_to_switch

</pre>
Git checkout is also used to move the HEAD pointer to a specific commit or switch between branches. It rollbacks any content changes to those of the specific commit. This will not make changes to the commit history. It has potential to overwrite files in the working directory.
<ul>
 	<li>git branch -d &lt;branch name&gt; - this command deletes a specific branch</li>
</ul>
<pre class="lang:default decode:true ">neo $git branch -d neo
Deleted branch neo (was 7d8e453).
neo $
</pre>
<ul>
 	<li>git branch -D &lt;branch name&gt; - this command forcefully deletes a specific branch in case the above command does not work. this can be case when code has been indexed/ committed but not pushed to remote</li>
</ul>
&nbsp;
<ul>
 	<li>diffmerge - this is a tool when there is a major conflict and sublime or any other code editor might not be the best solution. this can be downloaded from <a href="https://sourcegear.com/diffmerge/">here</a>.</li>
</ul>
<a href="http://analyticsbot.tk/wp-content/uploads/2018/11/img_merge_linux.png"><img class="size-medium wp-image-1135 aligncenter" src="http://analyticsbot.tk/wp-content/uploads/2018/11/img_merge_linux-300x188.png" alt="" width="300" height="188" /></a>
<ul>
 	<li>git status - this command is used to know the current status of the local repository</li>
</ul>
<pre class="lang:default decode:true ">neo $git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean</pre>
<ul>
 	<li>git checkout &lt;filename&gt; - discards changes to that file</li>
</ul>
<pre class="lang:default decode:true"># create a new file
neo $touch abc.txt

# write some dummy text inside
neo $vi abc.txt 

# index the file
neo $git add .

# commit the file
neo $git commit -m "message"
[master 8b95da4] message
 1 file changed, 1 insertion(+)
 create mode 100644 coursera_deep_learning/cnn/abc.txt

# remove the file from index/ commit
neo $git checkout abc.txt 

# git status shows nothing to commit
neo $git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
neo $
</pre>
<ul>
 	<li>git checkout . - discards all changes in working area</li>
 	<li>git reset head &lt;filename&gt; - this is used to return the entire working tree (in this case the specific file) to the last committed state. This will discard commits in a private branch or throw away uncommitted changes.</li>
 	<li>git reset head *</li>
 	<li>git reset HEAD~N - removes recent N commits</li>
 	<li>git reset --mixed HEAD~N (by default)- keep in working area</li>
 	<li>git reset --soft HEAD~N (by default) - keeps in staging area</li>
 	<li>git reset --hard HEAD~N (by default) - removes everything</li>
 	<li>git revert - Creates a new commit from a specified commit by inverting it. Hence, adds a new commit history to the project, but it does not modify the existing one.</li>
 	<li>git init - initializes a new repository locally which can be pushed</li>
 	<li>git config - adds the config such as username, email to git</li>
</ul>
<pre class="lang:default decode:true ">neo $git config
usage: git config [&lt;options&gt;]

Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
    -f, --file &lt;file&gt;     use given config file
    --blob &lt;blob-id&gt;      read config from given blob object

Action
    --get                 get value: name [value-regex]
    --get-all             get all values: key [value-regex]
    --get-regexp          get values for regexp: name-regex [value-regex]
    --get-urlmatch        get value specific for the URL: section[.var] URL
    --replace-all         replace all matching variables: name value [value_regex]
    --add                 add a new variable: name value
    --unset               remove a variable: name [value-regex]
    --unset-all           remove all matches: name [value-regex]
    --rename-section      rename section: old-name new-name
    --remove-section      remove a section: name
    -l, --list            list all
    -e, --edit            open an editor
    --get-color           find the color configured: slot [default]
    --get-colorbool       find the color setting: slot [stdout-is-tty]

Type
    --bool                value is "true" or "false"
    --int                 value is decimal number
    --bool-or-int         value is --bool or --int
    --path                value is a path (file or directory name)
    --expiry-date         value is an expiry date

Other
    -z, --null            terminate values with NUL byte
    --name-only           show variable names only
    --includes            respect include directives on lookup
    --show-origin         show origin of config (file, standard input, blob, command line)

neo $
</pre>
<strong>When to use RESET vs CHECKOUT vs REVERT to make changes?</strong>

Each of the above commands can be used to rollback changes and each of them has a specific purpose that I am aware of. Let's see the best use case of RESET - this is used when we want to specifically roll back changes that are committed but not pushed to remote and that too specific commits back.

CHECKOUT rollbacks all the changes to the file until the last successful commit that was pushed to remote.

REVERT is used when the changes were pushed to remote but should be rolled back.
