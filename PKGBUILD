# Script generated with Bloom
pkgdesc="ROS - This package is wrapping version of ROBOTIS Dynamxel SDK for ROS. The ROBOTIS Dynamixel SDK, or SDK, is a software development library that provides Dynamixel control functions for packet communication. The API is designed for Dynamixel actuators and Dynamixel-based platforms."
url='http://wiki.ros.org/dynamixel_sdk'

pkgname='ros-kinetic-dynamixel-sdk'
pkgver='3.5.4_1'
pkgrel=1
arch=('any')
license=('Apache-2.0'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-roscpp'
)

depends=('ros-kinetic-roscpp'
)

conflicts=()
replaces=()

_dir=dynamixel_sdk
source=()
md5sums=()

prepare() {
    cp -R $startdir/dynamixel_sdk $srcdir/dynamixel_sdk
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

