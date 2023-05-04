MT-install-notes.md
Last modified: 2023-05-04 12:22

# MT's install notes for python-geosupport
* This repo is forked from Ian Shiland's. Look there for the original.
* Mostly my fork is just for personal notes and stuff, like this file.
	* In my case, this is entirely for Linux installs. 
* To get this to work you need to install _2_ things:
	1. this python-geosupport python package for your local python
	2. geosupport from DCP which essentially becomes a library python-geosupport runs against.

## 1. Install this python-geosupport package
There are two ways to do this depending on what you have access to on your Linux box.

### The easy way; use pip:
* Note: setup.py as suggested by the package maintainer is both deprecated and seems to be able to only install to system, not local dir.
* Instead, cd into the python-geosupport directory and run:
	* ``` pip3 install ./ ```
	* (pip3 on debian systems.)
* pip will build and install the local repo package inside .local/ or wherever you keep your local python packages.
* pip uninstall python-geosupport will remove the package (like any other)

### The harder way; use setup.py:
* To install on DOHMH python server (which has no pip) you need to use setup.py included with this git repo. Since you also don't have permission to install the package to the system, you have to give setup.py the local install directory through an environment variable, like so:
	* ``` export INSTALL_DIR=\$HOME/.local/ ```
	* ``` python3 ./setup.py install --prefix=$INSTALL_DIR ```

## 2. Install geosupport
* Just download the latest Linux version from NYC DCP's Bytes of the Big Apple.
	* (Linux version is only available as a 64 bit version, pretty sure)
* Unzip geosupport, probably in your home directory is best. (The Linux version will create a directory to unzip into when you unzip it.)
* Optional: set the environment variables GEOFILES and LD_LIBRARY_PATH in your .bashrc so you don't have to set them every time you run (see Running.)


## Running:
* Before running, you have to set the environment variables GEOFILES and LD_LIBRARY_PATH so python-geosupport knows where geosupport was unzipped. 
	* (Unless geosupport releases some kind of major changes that fundamentally break how it works, this is ALL you have to do to upgrade to a newer version of geosupport used with python-geosupport.)
* Run python (often ```python3``` on the command line for many systems.)
	* If you get the error: ``` geosupport.error.GeosupportError: libgeo.so: cannot open shared object file: No such file or directory ``` that just means you haven't set your environment variables or haven't set them correctly.
		* (Ignore the warning about 64 bit-ness, that's irrelevant.)





