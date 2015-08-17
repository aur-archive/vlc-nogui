# Maintainer: Alexsandr Pavlov <kidoz at mail dot ru>

pkgname=vlc-nogui
_name=${pkgname%${pkgname#???}}
pkgver=2.0.5
pkgrel=1
pkgdesc="A multi-platform MPEG, VCD/DVD, and DivX player"
arch=('i686' 'x86_64')
url="http://www.videolan.org/vlc/"
license=('GPL')
depends=('a52dec' 'fluidsynth' 'libmtp' 'libdvbpsi' 'libxpm' 'libcdio'
         'libdca' 'libproxy' 'sdl_image' 'libdvdnav' 'mesa'
         'lua' 'v4l-utils' 'libcddb' 'smbclient' 'libmatroska' 'zvbi'
         'taglib' 'sysfsutils' 'libmpcdec' 'ffmpeg' 'faad2' 'libupnp'
         'libshout' 'libmad' 'fribidi' 'libmpeg2' 'libmodplug'  'xcb-util-keysyms'
         'ttf-freefont' 'libxv' 'libass' 'xdg-utils')
makedepends=('avahi' 'pkg-config' 'live-media' 'libnotify' 'libbluray'
             'flac' 'libtheora' 'alsa-lib' 'jack' 'udev'
             'libraw1394' 'libdc1394' 'libavc1394' 'libva' 'libpulse'
             'lirc-utils' 'gnutls' 'libcaca')
optdepends=('avahi: for service discovery using bonjour protocol'
            'libnotify: for notification plugin'
            'libdvdcss: for decoding encrypted DVDs'
            'lirc-utils: for lirc plugin'
            'libavc1394: for devices using the 1394ta AV/C'
            'libdc1394: for IEEE 1394 plugin'
            'libpulse: PulseAudio support'
            'vdpau-video: vdpau back-end for nvidia'
            'libva-driver-intel: back-end for intel cards'
            'libbluray: for Blu-Ray disks')
provides=('vlc')
conflicts=('vlc' 'vlc-plugin')
replaces=('vlc' 'vlc-plugin')
options=('!libtool')
source=(http://downloads.videolan.org/pub/videolan/${_name}/${pkgver}/${_name}-${pkgver}.tar.xz)
md5sums=('4f959c0766ada8cea5a72c65fce94ebe')

build() {
  cd "${srcdir}/${_name}-${pkgver}"

  sed -i -e 's:truetype/freefont:TTF:g' modules/text_renderer/freetype.c
   
  ./configure --prefix=/usr \
              --enable-faad \
              --enable-lirc \
              --enable-pvr \
              --enable-realrtsp \
              --disable-rpath \
              --disable-qt4 \
              --disable-skins2 \
              --disable-glx 
  make
}

package() {
  cd "${srcdir}/vlc-${pkgver}"
  
  make DESTDIR=${pkgdir}/ install

  rm -rf ${pkgdir}/usr/share/applications
  rm -rf ${pkgdir}/usr/share/apps
  rm -rf ${pkgdir}/usr/share/kde4
  rm -rf ${pkgdir}/usr/share/icons
  rm ${pkgdir}/usr/share/vlc/vlc.ico
}
