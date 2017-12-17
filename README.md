README - VIO: Visual-Inertial Odometry
======================================

What is VIO?
------------

VIO is a library of C++ classes that implement the visual-inertial odometry pipeline described in these papers:
 
 - C. Forster, L. Carlone, F. Dellaert, and D. Scaramuzza. On-Manifold Preintegration Theory for Fast and Accurate Visual-Inertial Navigation. IEEE Trans. Robotics, 33(1):1-21, 2016.
 - C. Forster, L. Carlone, F. Dellaert, and D. Scaramuzza. On-Manifold Preintegration Theory for Fast and Accurate Visual-Inertial Navigation. IEEE Trans. Robotics, 33(1):1-21, 2016.
 - L. Carlone, Z. Kira, C. Beall, V. Indelman, and F. Dellaert. Eliminating Conditionally Independent Sets in Factor Graphs: A Unifying Perspective based on Smart Factors. In IEEE Intl. Conf. on Robotics and Automation (ICRA), 2014.

Quickstart
----------

In the root library folder execute (if you changed the GTSAM install folder, you may need to redrect VIO to your-gtsam-install-folder/lib/cmake/GTSAM):

```
#!bash
$ mkdir build
$ cd build
$ cmake ../
$ make
$ make check
```

Notea: if you use MKL in gtsam, you may need to add to .bashrc a line similar to: source /opt/intel/parallel_studio_xe_2018/compilers_and_libraries_2018/linux/mkl/bin/mklvars.sh intel64
Note1b: sometimes you may need to add /usr/local/lib to LD_LIBRARY_PATH in ~/.bashrc (if you get lib not found errors at run or test time)
Note2: you may have to add %YAML:1.0 as first line in all YAML files :-(

Prerequisites:

- [GTSAM](https://bitbucket.org/gtborg/gtsam/overview/) >= 4.0 (Branch: `feature/ImprovementsIncrementalFilter`)
- [OpenCV](https://opencv.org/opencv-3-0.html) >= 3.0 (Installation instructions below)
- [OpenGV] Installation instructions below 

Installation of OpenCV
----------------------
- on Mac:
```
#!bash
$ homebrew install vtk (to check)
download opencv3.3.1 from https://opencv.org/releases.html
unzip and go to opencv3.3.1
$ mkdir build
$ cd build
$ cmake ../
$ sudo make install
```
- on Linux:
```
#!bash
$ sudo apt-get install libvtk5-dev   (libvtk6-dev in ubuntu 17.10)
$ sudo apt-get install libgtk2.0-dev 
$ sudo apt-get install pkg-config
download opencv3.3.1 from https://opencv.org/releases.html
unzip and go to opencv3.3.1
$ mkdir build
$ cd build
$ cmake -DWITH_VTK=On ..
$ sudo make -j8 install
$ sudo make -j8 test (optional - quite slow)
```

Installation of OpenGV
----------------------
- git clone https://github.com/laurentkneip/opengv (I did this in my "home/code/" folder)
- (not needed in latest version) open CMakeLists.txt and set INSTALL_OPENGV to ON (this can be also done using cmake-gui)
- using cmake-gui, set: the eigen version to the GTSAM one (for me: /Users/Luca/borg/gtsam/gtsam/3rdparty/Eigen). if you don't do so, very weird error appear (may be due to GTSAM and OpenGV using different versions of eigen!)
- in the opengv folder do:

```
#!bash
$ mkdir build
$ cd build
$ cmake ../
$ sudo make -j8 install
$ sudo make -j8 check
```


