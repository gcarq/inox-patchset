# Maintainer: Michael Egger <gcarq@archlinux.info>
# Contributor: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: Pierre Schmitz <pierre@archlinux.de>
# Contributor: Jan "heftig" Steffens <jan.steffens@gmail.com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

# Possible replacements are listed in build/linux/unbundle/replace_gn_files.py
# Keys are the names in the above script; values are the dependencies in Arch
declare -rgA _system_libs=(
  [ffmpeg]=ffmpeg
  [flac]=flac
  [harfbuzz-ng]=harfbuzz-icu
  [icu]=icu
  [libjpeg]=libjpeg
  [libpng]=libpng
  [libvpx]=libvpx
  [libwebp]=libwebp
  #[libxml]=libxml2    # https://bugs.archlinux.org/task/29939
  [libxslt]=libxslt
  [re2]=re2
  [snappy]=snappy
  [yasm]=
  [zlib]=minizip
)

pkgname=inox
pkgver=55.0.2883.87
pkgrel=1
_launcher_ver=3
pkgdesc="Chromium Spin-off to enhance privacy by disabling data transmission to Google"
arch=('i686' 'x86_64')
url="http://www.chromium.org/Home"
license=('BSD')
depends=('gtk2' 'nss' 'alsa-lib' 'xdg-utils' 'bzip2' 'ffmpeg' 'icu' 'libevent'
         'libxss' 'libexif' 'libjpeg' 'libpng' 'libgcrypt' 'ttf-font' 'systemd'
         'dbus' 'flac' 'snappy' 'libwebp' 'libxslt' 're2' 'minizip'
         'pciutils' 'libpulse' 'harfbuzz-icu' 'libsecret' 'libvpx'
         'perl' 'perl-file-basedir' 'desktop-file-utils' 'hicolor-icon-theme')
makedepends=('python2' 'gperf' 'yasm' 'mesa' 'ninja' 'git')
makedepends_x86_64=('lib32-gcc-libs' 'lib32-zlib')
optdepends=('kdebase-kdialog: needed for file dialogs in KDE'
            'gnome-keyring: for storing passwords in GNOME keyring'
            'kwallet: for storing passwords in KWallet')
install=inox.install
source=(https://commondatastorage.googleapis.com/chromium-browser-official/chromium-$pkgver.tar.xz
        chromium-launcher-$_launcher_ver.tar.gz::https://github.com/foutrelis/chromium-launcher/archive/v$_launcher_ver.tar.gz
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/inox.desktop
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-52.0.2743.116-unset-madv_free.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-system-ffmpeg-r4.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-icu58.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-widevine.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-battery-status-service.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-autofill-download-manager.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-google-url-tracker.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-default-extensions.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/modify-default-prefs.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-web-resource-service.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/restore-classic-ntp.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-google-ipv6-probes.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-gcm-status-check.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/add-duckduckgo-search-engine.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/branding.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/launcher-branding.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-missing-key-warning.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-translation-lang-fetch.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-update-pings.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-sandbox-pie.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-new-avatar-menu.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/disable-first-run-behaviour.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/fix-building-without-safebrowsing.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/product_logo_{16,22,24,32,48,64,128,256}.png)

sha256sums=('e81bd3140d9c84dfee04d9a94686dfe6a20ae79475d84f17154c5536dcb81a58'
            '8b01fb4efe58146279858a754d90b49e5a38c9a0b36a1f84cbb7d12f92b84c28'
            'ff3f939a8757f482c1c5ba35c2c0f01ee80e2a2273c16238370081564350b148'
            '3b3aa9e28f29e6f539ed1c7832e79463b13128863a02e9c6fecd16c30d61c227'
            'e3c474dbf3822a0be50695683bd8a2c9dfc82d41c1524a20b4581883c0c88986'
            'fad964da0295a6a7b4393778e717ebdfd37dec33fe78beb2c639abd3973deb7a'
            'd6fdcb922e5a7fbe15759d39ccc8ea4225821c44d98054ce0f23f9d1f00c9808'
            'c46e918f9e469aefdf4861967dcba98a30b3af0fedb5cb0f674efbdf253bc87a'
            'e64ec33773d31ea599ec3436a728f5a2d9a6a2c07e69ec70176d051a5144553a'
            'a7329d7f3099f6b8dfe4b7addeb7abbca1cf079139a86c6483a51fed0190478e'
            'b3fa783f09c5cd927d4af43c9c0a1f24744d840d5002c2e5a5c5af073fdbcf1b'
            '3a331e004ac84a493dced9a990f71119d3ef31ebbfd67b13a7ec194e835dea11'
            'c2bab92d8d237d341b79d868e814807c3f862d3b3c22a87bbf5e905853e516ae'
            'ed4471fa8a984ccea7fd1900a76865e65a8f5afb6a6390faa22a4758d77bbc07'
            '562eea848542f76537a9f3993bac397b523d0ce419416daf0bb4dd17f5203c7c'
            'b081462f645ffab7aaf2c310761c269329d3d22a36cf463dd0ba5ebb3da2141e'
            'e325c598fa3357d7eac10a7635b63e8f543cd77d60ffc299b32560861fc16e67'
            'bdb2b5c7174ddf71d1f172c7f99d2d11f3e62595756d31a587e1264308f7d67c'
            '8412971b2814c1135375d5e5fc52f0f005ac15ed9e7625db59f7f5297f92727e'
            '55b75daf5aad2a8929c80837f986d4474993f781c0ffa4169e38483b0af6e385'
            '37f9ad0b8d572378ad2c1c6c47d2135f76d5c15a20170bb1712d7bd40caf247e'
            '9e1ce0c47dd51595f13a6f611de39573022c7ff59fc003ab775a5319ebfedad8'
            'bb28fcc1a2fd37ee972b2b02014bbb467cc1baef85c9e6c998b11e97d47c9ac9'
            '9e37751dca4a2b60681ba14119bc3839685ae420686664de7dfc4245f9eeff3c'
            'c47efe038f502d4fe2b66e59347b01c58ee8739a8d8f050c6c1cc60752d24f13'
            '94a8bc6bc33c781c676da1fc4d2901a89e0c71c9284a007520d025a580e1cf36'
            '71471fa4690894420f9e04a2e9a622af620d92ac2714a35f9a4c4e90fa3968dd'
            '4a533acefbbc1567b0d74a1c0903e9179b8c59c1beabe748850795815366e509'
            '7b88830c5e0e9819f514ad68aae885d427541a907e25607e47dee1b0f38975fd'
            '8c10e3b03b13555b461add586422472e0a96d3af49a078d6d952bc0719ba9d94'
            'cc08b771d83b7434c3173c27419bc7d1d4ee375256f3169ef2b9333ba1f2beeb'
            '53a1e8da18069eb4d6ab3af9c923c22a0f020241a4839c3140e3601052ddf6ff'
            '896993987d4ef9f0ac7db454f288117316c2c80ed0b6764019afd760db222dad'
            '3df9b3bbdc07fde63d9e400954dcc6ab6e0e5454f0ef6447570eef0549337354')

prepare() {
  cd "$srcdir/chromium-$pkgver"

  # https://groups.google.com/a/chromium.org/d/topic/chromium-packagers/9JX1N2nf4PU/discussion
  touch chrome/test/data/webui/i18n_process_css_test.html

  # Enable support for the Widevine CDM plugin
  # libwidevinecdm.so is not included, but can be copied over from Chrome
  # (Version string doesn't seem to matter so let's go with "Pinkie Pie")
  sed "s/@WIDEVINE_VERSION@/Pinkie Pie/" ../chromium-widevine.patch |
    patch -Np1

  # Make it possible to remove third_party/adobe
  echo > "flapper_version.h"

  # Build fixes from Gentoo
  patch -Np1 -i ../chromium-system-ffmpeg-r4.patch
  patch -Np1 -i ../chromium-icu58.patch

  # Disable MADV_FREE (if set by glibc)
  # https://bugzilla.redhat.com/show_bug.cgi?id=1361157
  patch -Np1 -i ../chromium-52.0.2743.116-unset-madv_free.patch

  patch -Np1 -i ../fix-building-without-safebrowsing.patch

  # Apply Inox patches
  patch -Np1 -i ../disable-autofill-download-manager.patch
  patch -Np1 -i ../disable-google-url-tracker.patch
  patch -Np1 -i ../disable-default-extensions.patch
  patch -Np1 -i ../modify-default-prefs.patch
  patch -Np1 -i ../disable-web-resource-service.patch
  patch -Np1 -i ../restore-classic-ntp.patch
  patch -Np1 -i ../disable-google-ipv6-probes.patch
  patch -Np1 -i ../disable-gcm-status-check.patch
  patch -Np1 -i ../add-duckduckgo-search-engine.patch
  patch -Np1 -i ../branding.patch
  patch -Np1 -i ../disable-missing-key-warning.patch
  patch -Np1 -i ../disable-translation-lang-fetch.patch
  patch -Np1 -i ../disable-update-pings.patch
  patch -Np1 -i ../chromium-sandbox-pie.patch
  patch -Np1 -i ../disable-new-avatar-menu.patch
  patch -Np1 -i ../disable-first-run-behaviour.patch
  patch -Np1 -i ../disable-battery-status-service.patch

  # Work around bug in blink in which GCC 6 optimizes away null pointer checks
  # https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=833524
  # https://gcc.gnu.org/bugzilla/show_bug.cgi?id=68853#c2
  sed -i '/config("compiler")/ a cflags_cc = [ "-fno-delete-null-pointer-checks" ]' \
    build/config/linux/BUILD.gn

  # Use Python 2
  find . -name '*.py' -exec sed -i -r 's|/usr/bin/python$|&2|g' {} +
  # There are still a lot of relative calls which need a workaround
  mkdir -p "$srcdir/python2-path"
  ln -sf /usr/bin/python2 "$srcdir/python2-path/python"

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

  python2 third_party/libaddressinput/chromium/tools/update-strings.py

  # Patch Inox launcher
  cd "$srcdir/chromium-launcher-$_launcher_ver"
  patch -Np1 -i ../launcher-branding.patch
}

build() {
  make -C "$srcdir/chromium-launcher-$_launcher_ver" PREFIX=/usr

  cd "$srcdir/chromium-$pkgver"

  export PATH="$srcdir/python2-path:$PATH"
  export TMPDIR="$srcdir/temp"
  mkdir -p "$TMPDIR"

  local _flags=(
    'is_clang=false'
    'symbol_level=0'
    'is_debug=false'
    'fatal_linker_warnings=false'
    'treat_warnings_as_errors=false'
    'fieldtrial_testing_like_official_build=false'
    'remove_webcore_debug_symbols=true'
    'ffmpeg_branding="Chrome"'
    'proprietary_codecs=true'
    'link_pulseaudio=true'
    'linux_use_bundled_binutils=false'
    'use_cups=true'
    'use_gconf=false'
    'use_gnome_keyring=false'
    'use_gold=false'
    'use_gtk3=false'
    'use_kerberos=true'
    'use_pulseaudio=true'
    'use_sysroot=false'
    'enable_hangout_services_extension=false'
    'enable_widevine=true'
    'enable_nacl=false'
    'enable_nacl_nonsfi=false'
    'enable_rlz=false'
    'enable_rlz_support=false'
    'enable_remoting=false'
    'enable_google_now=false'
    'safe_browsing_mode=0'
    'enable_webrtc=false'
    'enable_hotwording=false'
    'enable_print_preview=false'
    )
  python2 tools/gn/bootstrap/bootstrap.py --gn-gen-args "${_flags[*]}"
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

  cp -a out/Release/{*.pak,*.bin,libwidevinecdmadapter.so} \
    "$pkgdir/usr/lib/$pkgname/"

  cp -a out/Release/locales "$pkgdir/usr/lib/$pkgname/"

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
