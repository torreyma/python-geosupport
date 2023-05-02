MT-install-notes.md
Last modified: 2023-05-02 11:57

Note: setup.py as suggested by the package maintainer is both deprecated and seems to be able to only install to system, not local dir.

Instead, cd into the python-geosupport directory and run:
pip3 install ./

(pip3 on debian systems.)
pip will build and install the local repo package.

pip uninstall python-geosupport will remove the package (like any other)


