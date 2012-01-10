.. Github Webinar - 2012.01.10 documentation master file, created by
   sphinx-quickstart on Tue Jan 10 09:34:34 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Session 2 (9:00a - 9:50a)
===========================

Committing code

Files being bumped out of stage (editing a file once it's staged)? Not really. What really happens? Why is the file shown in unstaged and staged? There are two sets of changes. Two scopes, file and content. Git separates them in to two sets of changes -- to see the difference:

``git diff``

compare to

``git diff --staged``

to see what's going on.

``git commit -v``

Interatcive add:

``git add -p``


