MT-install-notes.md
Last modified: 2023-05-02 15:46

Note: setup.py as suggested by the package maintainer is both deprecated and seems to be able to only install to system, not local dir.

Instead, cd into the python-geosupport directory and run:
pip3 install ./

(pip3 on debian systems.)
pip will build and install the local repo package.

pip uninstall python-geosupport will remove the package (like any other)

Note: you have to set the environment variables GEOFILES and LD_LIBRARY_PATH so python-geosupport knows where geosupport was unzipped. (Unless geosupport releases some kind of major changes, this is ALL you have to do to upgrade to a newer version of geosupport used with python-geosupport.)


