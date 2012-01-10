.. Github Webinar - 2012.01.10 documentation master file, created by
   sphinx-quickstart on Tue Jan 10 09:34:34 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===========================
Session 4 (12:00p - 2:00p)
===========================


Questions
=========

* Can you reset an individual file?

``git checkout -- <filename>``

``git checkout HEAD -- source/``

What's the difference between

``git checkout -- <filename>``

and

``git checkout HEAD -- <filename>``

Nothing, HEAD is assumed.


* Other questions on collaboration, binaries and design...


Netork Interactions
===================

Everything begins locally in git then layers on things like remotes and collaboration.

Almost all activities happen offline. Offline activities have to be pushed to remotes.


Cloning
-------

four primary protocols: file, git, ssh, http.


file
----

``git clone file:///path/to/project``

``git clone /path/to/project``

cloning a local file is like checkout, but clone grabs all history for a repository.

file:///path/to/project fires up the 'networking' code within git whereas just /path/to/project looks directly at the filesystem.

git
---

``git clone git://server/project.git``

Almost always read-only. Can be made writable, but in most cases it's read-only.

http (dumb)
-----------

``git clone http://server/project.git``

``git clone https://server/project.git``

Used to be the real differntiator between git and mercurial. Dumb version is insanely slow and inefficient.

https (smart)
-------------

Much faster and offers progress. Mostly handled on the server side.


Exercises
=========

Cloning and collaborating:

``git clone https://githubstudents:students987@github.com/githubstudents/hellogitworld.git``

``git branch evanculver``

``git push -u`` -- tells git to track it.


<BREAK>




Example of git's speed by adding 3000 files and pushing them to remote.

After pushing, we can almost instantly get references to those files, but they're just references.

``git fetch origin``
``git checkout thousands``

When checking out, the state of the filesystem is being modified. By switching between the ``thousands`` branch and mine, > 3000 files are being created/destroyed

"Once mastered, the concepts of local, remote and upstream branches, the rest falls into place"

Local and remote live on your box.

Typing ``git fetch``, your local cache is updated against what's upstream or remote to you.

``git fetch`` === ``git fetch origin``

Push
----

``git push <remote>``


Pull
----

0 collaboration up until this point. The integration point.

Combination: retrieves upstream objects and then merges and then commits merge to the local branch.


Excercise: Merging in remotes
-----------------------------

Merging:

``git merge remotes/origin/chance``

Pushing back up to remote:

``git push``

Reviewing any commits in the entire remotes tree:

``git log -2 remotes/origin/chance``


Remotes
-------

Simiply 'bookmarks' or pointers.

Origin is a remote you get by default.

``git remote -v``


Q: Why two entries?
A: One inbound and one outbound. Almost always the same, but can be different in a very unique situation. For example, you may want to pull all code over ssh but push all over http.

Adding a remote
---------------

``git remote add <remotename> <remotepath>``

``git remote add matthewongithub https://github.com/matthewmccullough/hellogitworld``

*note*: Remote branches are locally immutable.

We have to make a local branch for anything we would like to change.

``git checkout kenkil``

Git is smart enough to know that you probably wanted to actually checkout the remote (``remotes/origin/kenkil``).

If you look at ``.git/config``, you will see various ``[branch *]`` sections which define the remote/tracking portion of this.

Git will get mad if the branch name is ambiguous:

error: refspec... blah blah

``git checkout -b <localbranch> --track remotes/origin/richzurad``

Prune
-----

``git remote prune <remotename>`` -- only removes old branches that no longer exist on the remote, has to be given an explicit remote name.

Diff'ing against remotes (or any two things)
-------------------------------------------

``git diff origin/ericg``

``git diff origin/ericg origin/richzurad``


More exercises
--------------

<edit, add, commit>

``git reset --soft HEAD~1``

Tells git to roll back 1 commit, leaving the change in tact.

If you have already pushed, the game has changed entirely.

You can do the same as above, but force the push -- the consequences of forcing the push causes the graph of the commits changes as your peers see them.
Furthermore, you then have to ask what other people may be basing their work on. It may cause some really counter-intuitive output and attempts to merge in changes.

A better approach is to push another commit by 'reverting':

``git revert <commithash>`` -- Make a new commit that negates what was just committed. Always safe because it's always forward moving which is exactly why forcing commits and changing history/graphi is usually always bad.
