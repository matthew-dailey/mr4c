Installing on Fedora 21
=======================

These instructions are for Fedora 21, written on March 15, 2015.

### Installing Java dependencies
* Java (1.8.0_31)
 * Download the [Oracle JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and install.
 * Historically, the OpenJDK that comes with many Linux distros has not worked well with Hadoop.
 * Make sure to set `JAVA_HOME` to where you installed this.
* Ant (1.9.4)
 * Download a binary distribution from [ant](http://ant.apache.org/)
 * I tried the version in yum, but it did not have many required extensions (like JUnit) installed.
 * Make sure to set `ANT_HOME` to where you installed this.
* Ivy (2.4.0)
 * Download [ivy](http://ant.apache.org/ivy/download.cgi) binary release, and copy `ivy.jar` into `$ANT_HOME/lib`.
 * Test that ant and ivy are working by running `ant` in `$IVY_HOME/src/examples/hello-ivy`.

### Installing C++ Base dependencies
* g++ (4.9.2-6.fc21)
 * `sudo yum install gcc-c++`
* log4cxx (0.10.0-17.fc21)
 * `sudo yum install log4cxx-devel`
* cppunit (1.12.1-13.fc21)
 * `sudo yum install cppunit-devel`
* jansson (2.6-4.fc21)
 * `sudo yum install jansson-devel`
 * The library was already installed, but the devel headers were not

At this point, `make -C native` should work even without the GIS libraries or Java dependencies.

### Installing GIS dependencies
* proj4 (4.8.0-7.fc21)
 * `sudo yum install proj-devel`
* gdal (1.11.2-1.fc21)
 * `sudo yum install gdal-devel`
 * This installs the headers into `/usr/include/gdal/`, but the mr4c code does not expect the last `gdal` subdirectory
 * `sudo cp -i /usr/include/gdal/* /usr/include/`
 * Use `-i` to ensure any overwrites are confirmed by you
