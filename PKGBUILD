# Maintainer: Michael Egger <gcarq@archlinux.info>
# Contributor: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: Pierre Schmitz <pierre@archlinux.de>
# Contributor: Jan "heftig" Steffens <jan.steffens@gmail.com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

#########################
## -- Build options -- ##
#########################

_enable_vaapi=0  # VA-API hardware video acceleration, might be problematic with AMD and NVIDIA

# Possible replacements are listed in build/linux/unbundle/replace_gn_files.py
# Keys are the names in the above script; values are the dependencies in Arch
declare -rgA _system_libs=(
  #[ffmpeg]=ffmpeg           # https://crbug.com/731766
  [flac]=flac
  #[freetype]=freetype2      # https://crbug.com/pdfium/733
  [harfbuzz-ng]=harfbuzz-icu
  #[icu]=icu                 # Enable again when upstream supports ICU 59
  [libdrm]=
  [libjpeg]=libjpeg
  #[libpng]=libpng           # https://crbug.com/752403
  #[libvpx]=libvpx           # https://bugs.gentoo.org/611394
  [libwebp]=libwebp
  #[libxml]=libxml2          # https://bugs.gentoo.org/616818
  [libxslt]=libxslt
  [opus]=opus
  [re2]=re2
  [snappy]=snappy
  [yasm]=
  [zlib]=minizip
)

pkgname=inox
pkgver=60.0.3112.101
pkgrel=1
_launcher_ver=5
pkgdesc="Chromium Spin-off to enhance privacy by disabling data transmission to Google"
arch=('i686' 'x86_64')
url="https://www.chromium.org/Home"
license=('BSD')
depends=('gtk3' 'nss' 'alsa-lib' 'xdg-utils' 'libxss' 'libcups' 'libgcrypt'
         'ttf-font' 'systemd' 'dbus' 'libpulse' 'pciutils' 'json-glib'
         'desktop-file-utils' 'hicolor-icon-theme')
depends+=(${_system_libs[@]})
makedepends=('python2' 'gperf' 'yasm' 'mesa' 'ninja' 'nodejs' 'git')
optdepends=('pepper-flash: support for Flash content'
            'kdialog: needed for file dialogs in KDE'
            'gnome-keyring: for storing passwords in GNOME keyring'
            'kwallet: for storing passwords in KWallet')
install=inox.install
source=(https://commondatastorage.googleapis.com/chromium-browser-official/chromium-$pkgver.tar.xz
        chromium-launcher-$_launcher_ver.tar.gz::https://github.com/foutrelis/chromium-launcher/archive/v$_launcher_ver.tar.gz
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/inox.desktop
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-gn-bootstrap-r8.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-blink-gcc7.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-v8-gcc7.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-vaapi.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-widevine.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0001-fix-building-without-safebrowsing.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0003-disable-autofill-download-manager.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0004-disable-google-url-tracker.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0005-disable-default-extensions.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0006-modify-default-prefs.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0007-disable-web-resource-service.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0008-restore-classic-ntp.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0009-disable-google-ipv6-probes.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0010-disable-gcm-status-check.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0011-add-duckduckgo-search-engine.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0012-branding.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0013-disable-missing-key-warning.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0014-disable-translation-lang-fetch.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0015-disable-update-pings.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0016-chromium-sandbox-pie.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0017-disable-new-avatar-menu.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0018-disable-first-run-behaviour.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0019-disable-battery-status-service.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0020-launcher-branding.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/product_logo_{16,22,24,32,48,64,128,256}.png)

sha256sums=('0bfb6318af1c3cf82e8ac872e3da34cd3c013aadaab446d5097228101cec065e'
            '4dc3428f2c927955d9ae117f2fb24d098cc6dd67adb760ac9c82b522ec8b0587'
            'ff3f939a8757f482c1c5ba35c2c0f01ee80e2a2273c16238370081564350b148'
            '06345804c00d9618dad98a2dc04f31ef19912cdf6e9d6e577ef7ffb1fa57003f'
            'f94310a7ba9b8b777adfb4442bcc0a8f0a3d549b2cf4a156066f8e2e28e2f323'
            '46dacc4fa52652b7d99b8996d6a97e5e3bac586f879aefb9fb95020d2c4e5aec'
            'c454d6200e51f052dc301a98cf13e1c6989395975997d3d9671dd186a23bb709'
            'd6fdcb922e5a7fbe15759d39ccc8ea4225821c44d98054ce0f23f9d1f00c9808'
            '9036511e2e15b3587110601b671e6cdb1bb03bd03042db43b7393ed242b350d4'
            '293c31dc7df13bdef6087f839071c00dc096bfc93ffbce8615c2d157f0675033'
            'a9134b55d5521907f127e8e4e81e91a35226d55e9f034e7d589b357cf2566760'
            '26f50047ee9c7370492a42921132eeea02eab96f19f6df7949f409ccac514c28'
            '09393444a9c95a1f7f271bcc4876283fa75ff9660ff50c1db7c83f7addd8f1bc'
            'dcc54ea1548c75c3f054a37d123fdd5db75379ab94de908368a589c267e65dbe'
            '2a6e7853e40c0d71d38aea7b70032e538569e576de7896d722048c4ef5a758b2'
            '562eea848542f76537a9f3993bac397b523d0ce419416daf0bb4dd17f5203c7c'
            'f294fb136ab128d8b5dc866a858d061ff2a1aea593c4081ed7a5fdb0e85553bc'
            'e8a6893c82579f71095d8bb3808a24e39b17c97efc45d2fa783072c7a0a1f9d5'
            'c7904c2c31490673297e3d423ca91d925bf4b436928502de725d353b809bb8ca'
            '55b75daf5aad2a8929c80837f986d4474993f781c0ffa4169e38483b0af6e385'
            '5494090d3997a0939ba8cedb209ac454abe2b425fa4ebed1d872bfa99c595451'
            'd47347bcaeeb59e336fcaf4f2fd3a7c6950c01958cce29e969721069aa5276ad'
            '6d1d6d801cf80c1df2b4ce5f0d6a25190f4117d581ef7ba0e25a99ec765ecdd7'
            '888902c17b7de23eb6c979af2a262f7552c197fd96feb0e7e23e9160fc877741'
            'ef93487636bb3171f1f0325a24295142dd6c58937d4e916f6e5a20470ea4d3c7'
            '153b0f438b42550e33cb54a0176dd3685bcaa66953d42472c8e111c3f77a4f69'
            'bfa530d317a5de1d038fd63f16a23694abc7a953456b30ae57ac649676137a2a'
            'bc41d777ec81b130239e80cdf92ccfec5762dc73ff1f14fc0b4845aa12b1e4b2'
            '71471fa4690894420f9e04a2e9a622af620d92ac2714a35f9a4c4e90fa3968dd'
            '4a533acefbbc1567b0d74a1c0903e9179b8c59c1beabe748850795815366e509'
            '7b88830c5e0e9819f514ad68aae885d427541a907e25607e47dee1b0f38975fd'
            '8c10e3b03b13555b461add586422472e0a96d3af49a078d6d952bc0719ba9d94'
            'cc08b771d83b7434c3173c27419bc7d1d4ee375256f3169ef2b9333ba1f2beeb'
            '53a1e8da18069eb4d6ab3af9c923c22a0f020241a4839c3140e3601052ddf6ff'
            '3df9b3bbdc07fde63d9e400954dcc6ab6e0e5454f0ef6447570eef0549337354')

prepare() {
  cd "$srcdir/chromium-$pkgver"

  # Enable support for the Widevine CDM plugin
  # libwidevinecdm.so is not included, but can be copied over from Chrome
  # (Version string doesn't seem to matter so let's go with "Pinkie Pie")
  sed "s/@WIDEVINE_VERSION@/Pinkie Pie/" ../chromium-widevine.patch |
    patch -Np1

  # https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=853347
  patch -Np1 -i ../chromium-blink-gcc7.patch

  # https://bugs.chromium.org/p/chromium/issues/detail?id=614289
  patch -Np1 -i ../chromium-v8-gcc7.patch

  # Fixes from Gentoo
  patch -Np1 -i ../chromium-gn-bootstrap-r8.patch

  # VA-API
  if [ "${_enable_vaapi}" = 1 ]; then
    patch -Np1 -i ../chromium-vaapi.patch
  fi

  # Make it possible to remove third_party/adobe
  echo > "flapper_version.h"

  # Apply patches to fix building
  patch -Np1 -i ../0001-fix-building-without-safebrowsing.patch

  # Apply Inox patches
  patch -Np1 -i ../0003-disable-autofill-download-manager.patch
  patch -Np1 -i ../0004-disable-google-url-tracker.patch
  patch -Np1 -i ../0005-disable-default-extensions.patch
  patch -Np1 -i ../0006-modify-default-prefs.patch
  patch -Np1 -i ../0007-disable-web-resource-service.patch
  patch -Np1 -i ../0008-restore-classic-ntp.patch
  patch -Np1 -i ../0009-disable-google-ipv6-probes.patch
  patch -Np1 -i ../0010-disable-gcm-status-check.patch
  patch -Np1 -i ../0011-add-duckduckgo-search-engine.patch
  patch -Np1 -i ../0012-branding.patch
  patch -Np1 -i ../0013-disable-missing-key-warning.patch
  patch -Np1 -i ../0014-disable-translation-lang-fetch.patch
  patch -Np1 -i ../0015-disable-update-pings.patch
  patch -Np1 -i ../0016-chromium-sandbox-pie.patch
  patch -Np1 -i ../0017-disable-new-avatar-menu.patch
  patch -Np1 -i ../0018-disable-first-run-behaviour.patch
  patch -Np1 -i ../0019-disable-battery-status-service.patch

  # Use Python 2
  find . -name '*.py' -exec sed -i -r 's|/usr/bin/python$|&2|g' {} +

  # There are still a lot of relative calls which need a workaround
  mkdir -p "$srcdir/python2-path"
  ln -sf /usr/bin/python2 "$srcdir/python2-path/python"

  mkdir -p third_party/node/linux/node-linux-x64/bin
  ln -s /usr/bin/node third_party/node/linux/node-linux-x64/bin/

  # Remove bundled libraries for which we will use the system copies; this
  # *should* do what the remove_bundled_libraries.py script does, with the
  # added benefit of not having to list all the remaining libraries
  local _lib
  for _lib in ${!_system_libs[@]} ${_system_libs[libjpeg]+libjpeg_turbo}; do
    find -type f -path "*third_party/$_lib/*" \
      \! -path "*third_party/$_lib/chromium/*" \
      \! -path "*third_party/$_lib/google/*" \
      \! -path "*base/third_party/icu/*" \
      \! -regex '.*\.\(gn\|gni\|isolate\|py\)' \
      -delete
  done

  python2 build/linux/unbundle/replace_gn_files.py \
    --system-libraries "${!_system_libs[@]}"

  # Patch Inox launcher
  cd "$srcdir/chromium-launcher-$_launcher_ver"
  patch -Np1 -i ../0020-launcher-branding.patch
}

build() {
  make -C "chromium-launcher-$_launcher_ver"

  cd "$srcdir/chromium-$pkgver"

  export PATH="$srcdir/python2-path:$PATH"
  export TMPDIR="$srcdir/temp"
  mkdir -p "$TMPDIR"

  local _flags=(
    'is_clang=false'
    'clang_use_chrome_plugins=false'
    'symbol_level=0'
    'is_debug=false'
    'fatal_linker_warnings=false'
    'treat_warnings_as_errors=false'
    'fieldtrial_testing_like_official_build=true'
    'remove_webcore_debug_symbols=true'
    'ffmpeg_branding="Chrome"'
    'proprietary_codecs=true'
    'link_pulseaudio=true'
    'linux_use_bundled_binutils=false'
    'use_gtk3=true'
    'use_gconf=false'
    'use_gnome_keyring=false'
    'use_gold=false'
    'use_sysroot=false'
    'enable_hangout_services_extension=false'
    'enable_widevine=true'
    'enable_nacl=false'
    'enable_swiftshader=false'
    'enable_nacl_nonsfi=false'
    'enable_rlz=false'
    'enable_rlz_support=false'
    'enable_remoting=false'
    'enable_google_now=false'
    'safe_browsing_mode=0'
    'enable_hotwording=false'
    'enable_print_preview=false'
  )

  python2 tools/gn/bootstrap/bootstrap.py -s --no-clean
  out/Release/gn gen out/Release --args="${_flags[*]}" \
    --script-executable=/usr/bin/python2

  ninja -C out/Release chrome chrome_sandbox chromedriver widevinecdmadapter
}

package() {
  cd "$srcdir/chromium-launcher-$_launcher_ver"
  make PREFIX=/usr DESTDIR="$pkgdir" install-strip
  install -Dm644 LICENSE \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE.launcher"

  cd "$srcdir/chromium-$pkgver"

  install -D out/Release/chrome "$pkgdir/usr/lib/$pkgname/$pkgname"

  install -Dm4755 out/Release/chrome_sandbox \
    "$pkgdir/usr/lib/$pkgname/chrome-sandbox"

  install -D out/Release/chromedriver "$pkgdir/usr/lib/$pkgname/inoxdriver"

  cp -a \
    out/Release/{chrome_{100,200}_percent,resources}.pak \
    out/Release/{*.bin,libwidevinecdmadapter.so} \
    out/Release/icudtl.dat \
    out/Release/locales "$pkgdir/usr/lib/$pkgname/"

  install -Dm644 out/Release/chrome.1 "$pkgdir/usr/share/man/man1/$pkgname.1"

  install -Dm644 "$srcdir/$pkgname.desktop" \
    "$pkgdir/usr/share/applications/$pkgname.desktop"

  for size in 16 22 24 32 48 64 128 256; do
    install -Dm644 "$srcdir/product_logo_$size.png" \
      "$pkgdir/usr/share/icons/hicolor/${size}x${size}/apps/$pkgname.png"
  done

  ln -s /usr/lib/$pkgname/inoxdriver "$pkgdir/usr/bin/inoxdriver"

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
