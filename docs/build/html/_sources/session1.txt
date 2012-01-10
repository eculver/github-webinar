.. Github Webinar - 2012.01.10 documentation master file, created by
   sphinx-quickstart on Tue Jan 10 09:34:34 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Session 1 (8:00a - 8:50a)
===========================

Introduction, a little history.

git init <projectname>

.git folder contains entire commit history

user identity - separate from auth, merely who you are.

locally, there are no permissions present other than those of the filesystem itself.

git config
     --local = per repository
     --global = per user
     --system = per machine

     color.ui auto

     core.autocrlf input -- "This setting tells git to convert the newlines to the system’s standard when checking out files, and to LF newlines when committing in"

ssh-keygen -t rsa -C"<email> for <purpose>"

-C = comment
