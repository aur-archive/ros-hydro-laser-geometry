# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - This package contains a class for converting from a 2D laser scan as defined by sensor_msgs/LaserScan into a point cloud as defined by sensor_msgs/PointCloud or sensor_msgs/PointCloud2."
url='http://ros.org/wiki/laser_geometry'

pkgname='ros-hydro-laser-geometry'
pkgver='1.5.16'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-tf
  ros-hydro-roscpp
  ros-hydro-sensor-msgs
  ros-hydro-catkin
  ros-hydro-angles)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost
  eigen3)

ros_depends=(ros-hydro-tf
  ros-hydro-roscpp
  ros-hydro-angles
  ros-hydro-sensor-msgs)
depends=(${ros_depends[@]}
  python2-numpy
  boost
  eigen3)

_tag=release/hydro/laser_geometry/${pkgver}-${_pkgver_patch}
_dir=laser_geometry
source=("${_dir}"::"git+https://github.com/ros-gbp/laser_geometry-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
