impost0r
========

impost0r is a tool that lets you clone the contribution activity of
another Github user to your account.  
This is done by creating a repository with backdated commits in a
way that it resembles the source user's activity a closely as
possible.

impost0r was created as a successor to [ghdecoy](https://github.com/tickelton/ghdecoy)
(which in turn was inspired by [gitfiti](https://github.com/gelstudios/gitfiti))
and addresses the following shortcomings and features that were often
requested for its successor:
* Operating system independence: work on Linux and Windows
* more 'human looking' contributions than ghdecoy's random data
* no dependence on an existing git installation or other external tools

Demo
------------
There are some demo repositories at [ttn-dcy](https://github.com/ttn-dcy)
where you can see what ghdecoy can do for you.

For a video demonstration see the EXAMPLE below.

Dependencies
------------

ghdecoy.py requires at least Python 3.7 and [dulwich](https://www.dulwich.io/)
0.20.3.

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
* Username: your Github username
* Email: the email address associated with your Github account. It
is important that this address is correct since Github uses it to determine
which commits to display in your contribution calendar.
* Password: your Github password. The password is required to push the
created repository to Github. It will not be displayed on the command line
and is used exclusively for pushing.
* Repository: Your repository in Github in which the new commits are to
be created. The repository has to be cloneable without authentication and
it is advisable to use a dedicated repository just for impostor. Ideally
you just create a new public repository, tick the box for
'Initialize this repository with a README' so that is immediately
cloneable, and you are ready to go.
* Donor username: the Github username of the person who's activity data
you want to clone


Known issues and limitations
----------------------------

* the newly created commits will usually become visible on your
calendar withing minutes (according to Github it can take up to 24 hours!)
but the list with your years of activity at the bottom right of your
account's overview page can take much longer to get updated and for some
reason occasionally will not get updated at all. If the changes do not
become visible even after a couple of days, it usually helps to delete
the repository and run impost0r again.
* impost0r currently requires that the repository it creates its commits
in is publicy readable.
* even if there is an existing installation of git, impost0r will currently
not use its configuration (like username and email) but ask you to enter
the data explicitly.
* there is a bug in dulwich 0.20.5 which causes the following error:
The problem should be solved in newer versions of dulwich. As a workaround
until a fixed version is available installing in from git or downgrading
to 0.20.3 should work.
* cloning data from an user with several years of regular activity can
take a significant amount of time. E.g. cloning 10 years worth of 10+
contributions per day can take in excess of 30 minutes.


EXAMPLE
-------

![impost0r.py demo video](https://raw.githubusercontent.com/tickelton/impost0r/master/contrib/impost0r-demo.gif)


LICENSE
-------

impost0r is distributed under the terms of the ISC license.

See LICENSE for details.

