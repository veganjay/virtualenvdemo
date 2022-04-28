%title: Virtualenv / Venv Wrappers
%author: Jason Youzwak
%date: 2022-04-28

## What is a virtual environment?

History: Several years ago, I was watching a python tutorial.
^
I was understanding it, until the presenter typed in a strange command:
^
    $ workon project

What magic is this?

-----------------------------------------------------------------------

## What is a virtualenv?

To understand, we first need to know about about "virtualenv".

A virtualenv is a lightweight isolated "virtual environment"

Typical usage:

    $ virtualenv myproject
    $ source myproject/bin/activate

^
You might say:

- That's too much typing!
- I want all my environments in a single place!

-----------------------------------------------------------------------

## Enter virtualenvwrapper

Create an environment via:

    $ mkvirtualenv myproject

Activate the virtual environment by:

    $ workon myproject

All files are kept in $HOME/.virtualenvs/

    $ ls -ltrh ~/.virtualenvs/
    total 52K
    drwxr-xr-x 4 python python 4.0K Apr 24 20:11 myproject

More details on the [Virtualenv Wrapper Project page](https://virtualenvwrapper.readthedocs.io/)

-----------------------------------------------------------------------

## What is venv?

venv is very similar to virtualenv:

    $ python3 -m venv myproject
    $ source myproject/bin/activate

^
Okay, fine - but I want a venv wrapper!

I found bash aliases: https://gist.github.com/dbtek/fb2ddccb18f0cf63a654ea2cc94c8f19

Now you can:

    $ mkvenv myproject
    $ venv myproject

-----------------------------------------------------------------------

## What is the difference between virtualenv and venv?

- *virtualenv* requires a `pip install`.
- *venv* comes "batteries included" since Python 3.3:

Honestly, I had to look this up.

According to the [virtualenv project pagepage](https://virtualenv.pypa.io/en/stable/), 

Compared to virtualenv, the venv module does not have a many features, and:

- is slower (by not having the app-data seed method),
- is not as extendable,
- cannot create virtual environments for arbitrarily installed python versions (and automatically discover these),
- is not upgrade-able via pip,
- does not have as rich programmatic API (describe virtual environments without creating them).

-----------------------------------------------------------------------

## TLDR: My setup 

Configure bash aliases:

```
$ curl https://raw.githubusercontent.com/veganjay/virtualenvdemo/main/docker/bash_aliases \
  >> ~/.bash_aliases
$ source ~/.bash_aliases
```

Now use:

    $ mkvenv myproject
    $ venv myproject
    $ lsvenv
    $ rmvenv myproject
