MT-install-notes.md
Last modified: 2023-05-02 16:09

Note: setup.py as suggested by the package maintainer is both deprecated and seems to be able to only install to system, not local dir.

Instead, cd into the python-geosupport directory and run:
pip3 install ./

(pip3 on debian systems.)
pip will build and install the local repo package.

pip uninstall python-geosupport will remove the package (like any other)

To install on DOHMH python server (which has no pip) you need to use setup.py in this git repo. Since you also don't have permission to install the package to the system, you have to give setup.py the local install directory through an environment variable, like so:
export INSTALL_DIR=\$HOME/.local/
python3 ./setup.py install --prefix=$INSTALL_DIR



Note: before running, you have to set the environment variables GEOFILES and LD_LIBRARY_PATH so python-geosupport knows where geosupport was unzipped. (Unless geosupport releases some kind of major changes, this is ALL you have to do to upgrade to a newer version of geosupport used with python-geosupport.)




