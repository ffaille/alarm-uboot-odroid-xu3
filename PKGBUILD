# U-Boot: ODROID-XU3/XU4/HC1/HC2/MC1
# Maintainer: Kevin Mihelich <kevin@archlinuxarm.org>

buildarch=4

pkgname=uboot-odroid-xu3
pkgver=2020.01
pkgrel=1
pkgdesc="U-Boot for ODROID-XU3/XU4/HC1/HC2/MC1"
arch=('armv7h')
url='https://github.com/hardkernel/u-boot'
license=('GPL')
install=$pkgname.install
backup=('boot/boot.txt' 'boot/boot.scr')
makedepends=('bc' 'dtc145' 'git')
source=('https://github.com/hardkernel/u-boot/archive/refs/tags/travis/odroidxu3-108.tar.gz'
        '0001-fix-for-building-dtc-with-gcc-10.patch'
        'boot.txt'
        'mkscr')
md5sums=('50c0abd886ad863b5a126d13028dfd09'
         'a1c39b8e3da5c9eefcf0b8d3d5324193'
         '52306aa4cf2c3499ecfcea026fb2741c'
         '021623a04afd29ac3f368977140cfbfd')
_srcname=u-boot-travis-odroidxu3-108

prepare() {
  cd ${_srcname}

  patch -p1 -i ../0001-fix-for-building-dtc-with-gcc-10.patch
}

build() {
  cd ${_srcname}

  unset CFLAGS CXXFLAGS CPPFLAGS

  make distclean
  make odroid-xu3_config
  sed -i 's/CONFIG_IDENT_STRING=".*"/CONFIG_IDENT_STRING=" Arch Linux ARM"/' .config
  make EXTRAVERSION=-${pkgrel}
}

package() {
  cd ${_srcname}

  mkdir -p "${pkgdir}"/boot

  cp sd_fuse/* "${pkgdir}"/boot
  chmod +x "${pkgdir}"/boot/sd_fusing.sh

  tools/mkimage -A arm -O linux -T script -C none -n "U-Boot boot script" -d ../boot.txt "${pkgdir}"/boot/boot.scr
  cp ../{boot.txt,mkscr} "${pkgdir}"/boot
}