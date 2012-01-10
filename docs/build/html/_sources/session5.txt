.. Github Webinar - 2012.01.10 documentation master file, created by
   sphinx-quickstart on Tue Jan 10 09:34:34 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===========================
Session 5 (2:15p - 2:15p)
===========================

Creating a funky situation
--------------------------

``git checkout -b evanculver2``

<edit a particular line>

<add, commit>

``git checkout -b evanculver``

<edit same line as before>

<add, commit>

``git merge evanculver2``

EEEEK --> merge conflict

"Make the file appear as a logical combination of those two disparate pieces"


Pull requests and workflow
--------------------------

Pull requests aren't limited to cross-repository merges. Pull requests make perfect sense within a single repository for forced code-review.


Rebase
------

Simulates members taking turns working? Actually not stupid, just sounds ridiculous.

Branching: you usually wait as long as possible to branch, and you try to get your changes merged back in as soon as possible (because your VCS sucks).

Rebasing rewrites history, keeps a consistent, straight history.

Merge commits become integration commits by layering merges on to the end via fast-forward (instead of merge made by recursive).

Fast-forward means that only one of the two branches changed since the branch occurred.

No merge commits are created.

``git checkout feature/some-feature``
``git rebase master``

"Take all of the stuff in the feature branch, hibernate it, delete it, start it at the end of master then replay all of the work in the feature branch on master."

"Rework your work so that it makes more sense for your team."

``git checkout feature/some-feature``
``git rebase -i HEAD~5``

"Rebase seems like a tool to replay history."




