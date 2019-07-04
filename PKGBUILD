# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - A rosout GUI viewer developed at Southwest Research Insititute as an alternative to rqt_console."
url='https://wiki.ros.org/swri_console'

pkgname='ros-melodic-swri-console'
pkgver='1.1.0'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-melodic-rosgraph-msgs
  ros-melodic-roscpp
  ros-melodic-rosbag-storage
  ros-melodic-catkin)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost
  qt5-base)

ros_depends=(ros-melodic-rosgraph-msgs
  ros-melodic-roscpp
  ros-melodic-rosbag-storage)
depends=(${ros_depends[@]}
  boost
  qt5-base)

# Git version (e.g. for debugging)
# _tag=release/melodic/swri_console/${pkgver}-${_pkgver_patch}
# _dir=${pkgname}
# source=("${_dir}"::"git+https://github.com/swri-robotics-gbp/swri_console-release.git"#tag=${_tag})
# sha256sums=('SKIP')

# Tarball version (faster download)
_dir="swri_console-release-release-melodic-swri_console-${pkgver}-${_pkgver_patch}"
source=("${pkgname}-${pkgver}-${_pkgver_patch}.tar.gz"::"https://github.com/swri-robotics-gbp/swri_console-release/archive/release/melodic/swri_console/${pkgver}-${_pkgver_patch}.tar.gz")
sha256sums=('3b316832e42c12ebf733b8f9f299ad56326bdeea281c36e1323dfe6c195a4cfe')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
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
