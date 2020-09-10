impost0r
========

impost0r is a tool that lets you clone the contribution activity of
another GitHub user to your account.  
This is done by creating a repository with backdated commits in a
way that it resembles the source user's activity a closely as
possible.

impost0r was created as a successor to [ghdecoy](https://github.com/tickelton/ghdecoy)
(which in turn was inspired by [gitfiti](https://github.com/gelstudios/gitfiti))
and addresses the following shortcomings and features that were often
requested for its successor:
* Operating system independence: work on Linux and Windows.
* More 'human looking' contributions than ghdecoy's random data.
* No dependence on an existing git installation or other external tools.

Demo
------------

![impost0r-before-after.png](https://gitlab.com/tickelton/impost0r/raw/master/contrib/impost0r-before-after.png)


A demo repository where you can see what commits generated by impost0r look
like is available at https://github.com/impost0rdemo/demo

For a video demonstration see the EXAMPLE below.

Dependencies
------------

ghdecoy.py requires at least Python 3.7 and [dulwich](https://www.dulwich.io/)
0.20.6.

Supported Operating Systems
---------------------------

ghdecoy is developed and tested on Linux and Windows 10.  
MacOS an other Unix-like operating systems should work but are not
officially supported.

Installation
------------

On Linux you can simply install the requirements and run
impost0r.py directly from the repository. No further installation
is required:

```shell
cd impost0r
pip install -r requirements.txt
python3 impost0r.py
```

On Windows 10 impost0r can be run just like on Linux if you
have a working installation of Python 3.7 or newer.  
Alternatively binary releases for Windows that do not require
a separate Python installation can be found at:
https://github.com/tickelton/impost0r/releases  
When using the binary release no installation is required either.
You can just extract the zip archive and run impost0r.exe. 

Usage
-----

When running impost0r it will ask for all required parameters on
the command line.  
The followin data are required:  
* Username: your GitHub username
* Email: the email address associated with your GitHub account. It
is important that this address is correct since GitHub uses it to determine
which commits to display in your contribution calendar.
* Password: your GitHub password. The password is required to push the
created repository to GitHub. It will not be displayed on the command line
and is used exclusively for pushing.
* Repository: Your repository in GitHub in which the new commits are to
be created. The repository has to be cloneable without authentication and
it is advisable to use a dedicated repository just for impostor. Ideally
you just create a new public repository, tick the box for
'Initialize this repository with a README' so that is immediately
cloneable, and you are ready to go.
* Donor username: the GitHub username of the person who's activity data
you want to clone


Known issues and limitations
----------------------------

* The newly created commits will usually become visible on your
calendar withing minutes (according to GitHub it can take up to 24 hours!)
but the list with your years of activity at the bottom right of your
account's overview page can take much longer to get updated and for some
reason occasionally will not get updated at all. If the changes do not
become visible even after a couple of days, it usually helps to delete
the repository and run impost0r again.  
***NOTE:*** To other users only the years of activity since the
creation of your account will be visible in your timeline. Only you
yourself will see an extended list going back to commits in your
repositories that were created before your registration.
* impost0r currently requires that the repository it creates its commits
in is publicy readable.
* Even if there is an existing installation of git, impost0r will currently
not use its configuration (like username and email) but ask you to enter
the data explicitly.
* There is a bug in dulwich 0.20.4 and 0.20.5 which causes the following error:  
      Creating and pushing new commits ...
      Traceback (most recent call last):00.0%
        File "/home/mint/dev/impost0r/impost0r.py", line 314, in <module>
          main()
        File "/home/mint/dev/impost0r/impost0r.py", line 303, in main
          porcelain.push(repo_tmpdir, push_url, 'master', outstream=err_stream, errstream=err_stream)
        File "/media/ramdisk/venv/lib/python3.8/site-packages/dulwich/porcelain.py", line 996, in push
          (ref, error.encode(err_encoding)))
      AttributeError: 'NoneType' object has no attribute 'encode'
The problem is solved in versions 0.20.6 of dulwich.
* Cloning data from an user with several years of regular activity can
take a significant amount of time. E.g. cloning 10 years worth of 10+
contributions per day can take in excess of 30 minutes.
* For several reasons it is often not possible to create a contribution
calendar that is an exact copy of that of another user. E.g. if you
already have some contributions of your own and the number of contributions
on a particular day exceeds the maximum number of single day contributions
in the donor's calendar the colors in your calendar will probably be off
after running impost0r.
* ***CAUTION:*** Do not try to copy the data from https://github.com/tickelton
since this account is used to occasionally test new features for impost0r.
Cloning its history can therefore lead to unintended side effects!


EXAMPLE
-------

![impost0r.py demo video](https://gitlab.com/tickelton/impost0r/raw/master/contrib/impost0r-demo.gif)


LICENSE
-------

impost0r is distributed under the terms of the ISC license.

See LICENSE for details.

