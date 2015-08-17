# Maintainer: PyrO_70 <brieuc.roblin at gmail dot com>
pkgname=ucpufreq-git
pkgver=20121013
pkgrel=1
pkgdesc="Daemon providing userland access to Cpufreq using DBus."
arch=('i686' 'x86_64')
url="http://www.pyrotools.org/"
license=('GPL')
depends=('qt4' 'cpupower')
makedepends=('git' 'qt4')
privides=('ucpufreq')
conflicts=('ucpufreq')

_gitroot="git://gitorious.org/ucpufreq/ucpufreq.git"
_gitname="ucpufreq"

build() {
  cd "$srcdir"

  msg2 "Connecting to gitorious ..."

  if [ -d $_gitname ] ; then
    ( cd $_gitname && git pull )
  else
    git clone $_gitroot $_gitname || return 1
  fi

  msg2 "Starting make..."
  
  cd "$_gitname"

  qmake "INSTALL_PREFIX=/usr" "DBUS_PREFIX=/" "USE_CPUPOWER=1" || return 1
  make || return 1
  make "INSTALL_ROOT=$pkgdir" install || return 1

} 
