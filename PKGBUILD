# Script generated with Bloom
pkgdesc="ROS - <p>Library to read, manipulate and write RT system profiles using the RTSProfile XML schema.</p>"
url='http://ros.org/wiki/openrtm_tools'

pkgname='ros-kinetic-rtsprofile'
pkgver='2.0.0_1'
pkgrel=1
arch=('any')
license=('EPL'
)

makedepends=('omniorbpy'
'python2-distribute'
'ros-kinetic-catkin'
)

depends=()

conflicts=()
replaces=()

_dir=rtsprofile
source=()
md5sums=()

prepare() {
    cp -R $startdir/rtsprofile $srcdir/rtsprofile
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

