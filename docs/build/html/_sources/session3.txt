.. Github Webinar - 2012.01.10 documentation master file, created by
   sphinx-quickstart on Tue Jan 10 09:34:34 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===========================
Session 3 (10:00a - 10:50a)
===========================

Viewing history

Git log
=======

No options: reverse chronological order. Automatically piped to pager.

Rarely used with no options.

``git log --stat`` -- shows files that participted in each commit. Commit hash, author, date, files, +/- for lines per change.

Extremely tedius to page our way back through changes.

Milestone marker for class: if we stopped now, you should have a pretty good basic workflow for getting around day-to-day.

More advanced usage::

``git log --diff-filter=A`` -- Same filters as ``git diff``

``git log --pretty=raw`` -- raw, full, fuller, and even custom with sprintf

``git log -3`` -- limits number of commits to 3 in this case.

``git log --author=evan@wiredrive.com`` -- all commits authored by me.

``git log --author=Evan`` -- all commits by me by using my name.


Ignoring Files
==============

Flat text file called .gitignore

Per project: in project root

Example::

    *.log
    *.tmp

Ignores all files with .log and .tmp exensions.

*Note*
``git status -u`` -- show me all files, don't simplify, lists out all files below folders.

Applies, at evaluation time in memory.

You can add .gitignore files to subfolders, behave like .gitconfig:

Top has weakest precidence, bottom has highest precidence.

They're evaluated as if concatenated end-to-end.

.gitignore can exist in any number of directories and subdirectories with no limit.

Git does not track empty directories.

How do you track empty directories? "holding it open with a toothpick."

Usually the easiest way is to touch a .gitignore in that directory.

Preconfigured .gitignore files: https://github.com/github/gitignore

System-wide?

``git config --global core.excudesfile "~/.gitignore"``

Have to enable, can't just create the file.

Removing Files
==============

Closure to the add command

Basis for refactoring and renaming

``rm <filename>``

``git rm <filename>`` -- put deletion into staging, if file doensn't exist, just adds deletion to staging area

*example*::
    rm <files>
    git add -u .

``git add -u`` grabs all removed files.

``git rm <fileame>`` removes the file and stages that file.

If you want it back:

``git reset --hard`` -- we'll come back to this, but it returns everything that is tracked to their last committed state. Blows away everything that's staged.

*note:* untracked files are untouched.

There is no ``move`` primitive in git.

``git mv <src> <dst>`` -- a 'composed' command for convenience.

Same as::

    ``mv <src> <dst> ; git add <dst>``

Rename flagged as soon as file is re-added. Git is good at detecting similar content.

There's a pretty funny discussion on the git mailinglist as to why there is no move primitive. Might be worth a look. (See slides).

``git log --stat -M`` -- shows renames in history.

Mindset should be that no matter how accurate we are when committing to history, there's always a chance that the committer has been mistaken at commit time. Just move it to the display layer.

Q: Can you set a threshold on the similarity filter?
A: Yes, ``git log --stat -M90``.

``git log -2 --stat -C --find-copies-harder`` -- Tells it to look harder for copy detection on top of rename detection.

This stuff can be used for the simplification of merges and is relevant for refactoring.
