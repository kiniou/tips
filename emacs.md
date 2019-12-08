# Emacs

## Tramp is asking constantly for password when editing Python file with sudo:

If anaconda-mode can't find ipython{2,3} in the sudo environment PATH, then it will trigger Tramp continuously to ask password.

Solution: just `apt-get install ipython`
