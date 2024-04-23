MT-install-notes.md
Last modified: 2024-04-23 16:50

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
    * (For some reason I have trouble getting these variables to work on fish. If you are getting the "libgeo.so: cannot open shared object file" error (see below) and you are running fish with your variables (supposedly) set, try running in bash (and setting variables), at least for testing purposes. 
    * ```MT-local-lib-config-commands.sh``` SHOULD set the variables for you (in bash), but seems like it doesn't. Try copying and pasting the export commands to set the variables. (Check with ```echo $GEOFILES``` as usual.)
* Run python interactively (often ```python3``` on the command line for many systems.)
* In python, import the library with ``` from geosupport import Geosupport ```
	* Tricky thing to watch out for: 
		* If you get the error ``` ModuleNotFoundError: No module named 'geosupport' ``` then python doesn't think python-geosupport is installed.
		* You may have installed it wrong. But you also need to be sure you are using python from anaconda. On some systems, like the DOHMH server, there can be more than one version of python3 installedm, and the system version can be old and/or missing a important bits.
		* Check you are using anaconda's python with ``` which python3 ``` --- it should show python3 being in /opt/anaconda/bin/python3 not /usr/bin or anywhere else.
		* If you discover you are using /usr/bin/python3 then you are probably in a non-login shell that is not sourcing the system bashrc (/etc/bashrc) where python3 is set to the anaconda version.
		* (For me this manifested in vim :terminal, but this problem could crop up other places. It does look like terminal on Jupyterhub is login though.)
* Create a geosupport object called 'g' with  ``` g = Geosupport() ```
	* Another tricky thing to watch out for: if at this point you get the error: ``` geosupport.error.GeosupportError: libgeo.so: cannot open shared object file: No such file or directory ``` that just means you haven't set your environment variables or haven't set them correctly.
		* (Ignore the warning about 64 bit-ness, that's irrelevant.)





