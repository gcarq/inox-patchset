# Maintainer: Michael Egger <gcarq@archlinux.info>
# Contributor: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: Pierre Schmitz <pierre@archlinux.de>
# Contributor: Jan "heftig" Steffens <jan.steffens@gmail.com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=inox
pkgver=64.0.3282.186
pkgrel=1
_launcher_ver=5
pkgdesc="Chromium Spin-off to enhance privacy by disabling data transmission to Google"
arch=('x86_64')
url="https://www.chromium.org/Home"
license=('BSD')
depends=('gtk3' 'nss' 'alsa-lib' 'xdg-utils' 'libxss' 'libcups' 'libgcrypt'
         'ttf-font' 'systemd' 'dbus' 'libpulse' 'pciutils' 'json-glib'
         'desktop-file-utils' 'hicolor-icon-theme')
makedepends=('python2' 'gperf' 'yasm' 'mesa' 'ninja' 'nodejs' 'git' 'libva'
             'clang' 'llvm' 'lld')
optdepends=('pepper-flash: support for Flash content'
            'kdialog: needed for file dialogs in KDE'
            'gnome-keyring: for storing passwords in GNOME keyring'
            'kwallet: for storing passwords in KWallet'
            'libva-intel-driver: for hardware video acceleration with Intel GPUs'
            'libva-mesa-driver: for hardware video acceleration with AMD/ATI GPUs'
            'libva-vdpau-driver: for hardware video acceleration with NVIDIA GPUs')
install=inox.install
source=(https://commondatastorage.googleapis.com/chromium-browser-official/chromium-$pkgver.tar.xz
        chromium-launcher-$_launcher_ver.tar.gz::https://github.com/foutrelis/chromium-launcher/archive/v$_launcher_ver.tar.gz
        chromium-$pkgver.txt::https://chromium.googlesource.com/chromium/src.git/+/$pkgver?format=TEXT
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/product_logo_{16,22,24,32,48,64,128,256}.png
        # Patches from Arch Linux
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-use-fromUTF8-for-UnicodeString-construction.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-omnibox-unescape-fragment.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-skia-harmony.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-widevine.patch
        # Patches from Gentoo
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-clang-r2.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-memcpy-r0.patch
        # Misc
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-vaapi-move.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-vaapi-init.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-vaapi-rgbx.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-vaapi-r16.patch
        # Inox patchset
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0001-fix-building-without-safebrowsing.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0002-fix-building-without-reporting.patch
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
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0021-disable-rlz.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/9000-disable-metrics.patch)
sha256sums=('5fd0218759231ac00cc729235823592f6fd1e4a00ff64780a5fed7ab210f1860'
            '4dc3428f2c927955d9ae117f2fb24d098cc6dd67adb760ac9c82b522ec8b0587'
            'e73f69942af1ba730a700151973fa6309b0586ff45bf35a7fea43f52b54a9cb5'
            '71471fa4690894420f9e04a2e9a622af620d92ac2714a35f9a4c4e90fa3968dd'
            '4a533acefbbc1567b0d74a1c0903e9179b8c59c1beabe748850795815366e509'
            '7b88830c5e0e9819f514ad68aae885d427541a907e25607e47dee1b0f38975fd'
            '8c10e3b03b13555b461add586422472e0a96d3af49a078d6d952bc0719ba9d94'
            'cc08b771d83b7434c3173c27419bc7d1d4ee375256f3169ef2b9333ba1f2beeb'
            '53a1e8da18069eb4d6ab3af9c923c22a0f020241a4839c3140e3601052ddf6ff'
            '896993987d4ef9f0ac7db454f288117316c2c80ed0b6764019afd760db222dad'
            '3df9b3bbdc07fde63d9e400954dcc6ab6e0e5454f0ef6447570eef0549337354'
            'f846218089a7b095d275e9cb3b74b28586d72f2137968c8c4e09b6f8232d694b'
            '814eb2cecb10cb697e24036b08aac41e88d0e38971741f9e946200764e2401ae'
            'feca54ab09ac0fc9d0626770a6b899a6ac5a12173c7d0c1005bc3964ec83e7b3'
            'd6fdcb922e5a7fbe15759d39ccc8ea4225821c44d98054ce0f23f9d1f00c9808'
            '4495e8b29dae242c79ffe4beefc5171eb3c7aacb7e9aebfd2d4d69b9d8c958d3'
            'f6227987c30f8b8a1e0cb5f3863698543a890e6f4bd20ff9384735e1122e66da'
            '1336c9a790c0bd7fa8cc00d0c58d6f6374cc311beb1a9db0a1696f4ddb21bfde'
            '8a81a14af625c8b79006d1b9b4321d5487bc2e56a3fb3a677f9a8dab369be7af'
            '0a9186ab591773f8fb6cbc908f9bbf4bc1508f1095b6c1cd7479aac945045373'
            'b82047df666e6bbf66e0c0911d20c5001bd1100fd08adafa92cac5f02a887a01'
            'd1e112adb135a823907aae33b189cb775d48e6afa785a26a452fc833824cd2e8'
            '300a7f3f0aba2037d159e5815f5cb3f2699c0ac26cbbb61209bbf01ac1eb2efb'
            '605cca8be9828a29cc96d473847eef9452d572fe6a56dacd96426a202310ba58'
            'fb91a7e30e2615e4eb0626b0fdcf97b92d4a727a52023730f408b02fee436c8d'
            '6ba0ad7d91b2f3bbf03fc4a3236a04310a0c57505e1688c7e11ace9dcea1dded'
            '2e8ba84204840f5f57b68456a70895c7ab07286efb4b165911e3f0c8072ded62'
            '7781ecd43e3c28f7d1e9158e043d6f98a190b5ee3c2c5ebe91644ea27e0b42ee'
            'daf9dcbeed8c6cd5d0012086680e8ee252121f56d96624d920d5b46d300a4052'
            'cf050473adae5b83680346b369997b5ead55dce282515f185e4096c5ed39f11d'
            '3190a507dfa00e863a0e622b5738db5cf19947f696ac7a790f427510cc15d1e1'
            '476593cf1e3bbf2539732567a70b0acea14033370317baf868f3d9701e4a1d5d'
            '0b7332739e7f5eabb54213449fabed35e98d46c334a9e15398582659755a89c3'
            'c79f12e444d2c7b9b61de8d6698033cc8a84bb35f949908b3a366105367237b0'
            'f80106b8127b60a62c006653154a26ebe68dd4aec5c551bae5321fa4e5ccef3f'
            '795686bf0dd7bfac0f596155be8fc7ed3f6294a6b764f793cd1614085562ce38'
            '5dc10c49cfc3ea65505e07366420eda0fc4878d0b0cebbfbcd8ad7daa88b3ded'
            'a1a5cb2c68abb02e7cdad3108a5a4d00beac86ae9341df98eb20495fcc400d45'
            'cb2bd17fbbd9184f15eb24d3b23deca92d06cb4b9ec31bd6944504e130d69ff8'
            'c17556772059a64873ddac383f2976e3befb5c07c3019b641c989ffb5683c4cd'
            '80d2974001708c288a54c24e1dc896ef25916552b740765f6066a244c05ffcd5'
            'dbe942b1eaba525ca6b81d398462a70360fc2043cbfe5d4105657c3bd721e592'
            '52412cb1da3169f246bb99f1299c91e1da3c14ca23876475918f534bb887f8c4')

# Possible replacements are listed in build/linux/unbundle/replace_gn_files.py
# Keys are the names in the above script; values are the dependencies in Arch
readonly -A _system_libs=(
  #[ffmpeg]=ffmpeg            # https://crbug.com/731766
  [flac]=flac
  #[fontconfig]=fontconfig    # Enable for M65
  #[freetype]=freetype2       # Using 'use_system_freetype=true' until M65
  #[harfbuzz-ng]=harfbuzz     # Using 'use_system_harfbuzz=true' until M65
  [icu]=icu
  [libdrm]=
  [libjpeg]=libjpeg
  #[libpng]=libpng            # https://crbug.com/752403#c10
  [libvpx]=libvpx
  [libwebp]=libwebp
  #[libxml]=libxml2           # https://crbug.com/736026
  [libxslt]=libxslt
  [opus]=opus
  [re2]=re2
  [snappy]=snappy
  [yasm]=
  [zlib]=minizip
)
readonly _unwanted_bundled_libs=(
  ${!_system_libs[@]}
  ${_system_libs[libjpeg]+libjpeg_turbo}
  freetype
  harfbuzz-ng
)
depends+=(${_system_libs[@]} freetype2 harfbuzz)

prepare() {
  cd "$srcdir/chromium-$pkgver"

  msg2 'Applying build patches'
  # https://crbug.com/710701
  local _chrome_build_hash=$(base64 -d ../chromium-$pkgver.txt |
    grep -Po '^parent \K[0-9a-f]{40}$')
  if [[ -z $_chrome_build_hash ]]; then
    error "Unable to find Chrome build hash."
    return 1
  fi
  echo "LASTCHANGE=$_chrome_build_hash-" >build/util/LASTCHANGE

  # Enable support for the Widevine CDM plugin
  # libwidevinecdm.so is not included, but can be copied over from Chrome
  # (Version string doesn't seem to matter so let's go with "Pinkie Pie")
  sed "s/@WIDEVINE_VERSION@/Pinkie Pie/" ../chromium-widevine.patch |
    patch -Np1

  # https://crbug.com/772655
  patch -Np1 -i ../chromium-use-fromUTF8-for-UnicodeString-construction.patch

  # https://crbug.com/789163
  patch -Np1 -i ../chromium-omnibox-unescape-fragment.patch

  # https://crbug.com/skia/6663#c10
  patch -Np4 -i ../chromium-skia-harmony.patch

  # Fixes from Gentoo
  patch -Np1 -i ../chromium-memcpy-r0.patch
  patch -Np1 -i ../chromium-clang-r2.patch

  # Remove compiler flags not supported by our system clang
  sed -i \
    -e '/"-Wno-enum-compare-switch"/d' \
    -e '/"-Wno-null-pointer-arithmetic"/d' \
    -e '/"-Wno-tautological-unsigned-zero-compare"/d' \
    -e '/"-Wno-tautological-constant-compare"/d' \
    build/config/compiler/BUILD.gn

  msg2 'Applying VA-API patches'
  patch -Np1 -i ../chromium-vaapi-move.patch
  patch -Np1 -i ../chromium-vaapi-init.patch
  patch -Np1 -i ../chromium-vaapi-rgbx.patch
  patch -Np1 -i ../chromium-vaapi-r16.patch

  msg2 'Applying Inox patchset'
  # Apply patches to fix building
  patch -Np1 -i ../0001-fix-building-without-safebrowsing.patch
  patch -Np1 -i ../0002-fix-building-without-reporting.patch

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
  patch -Np1 -i ../0021-disable-rlz.patch
  patch -Np1 -i ../9000-disable-metrics.patch

  # Use Python 2
  find . -name '*.py' -exec sed -i -r 's|/usr/bin/python$|&2|g' {} +

  # There are still a lot of relative calls which need a workaround
  mkdir -p "$srcdir/python2-path"
  ln -s /usr/bin/python2 "$srcdir/python2-path/python"

  # Setup nodejs dependency
  mkdir -p third_party/node/linux/node-linux-x64/bin
  ln -s /usr/bin/node third_party/node/linux/node-linux-x64/bin/

  # Remove bundled libraries for which we will use the system copies; this
  # *should* do what the remove_bundled_libraries.py script does, with the
  # added benefit of not having to list all the remaining libraries
  local _lib
  for _lib in ${_unwanted_bundled_libs[@]}; do
    find -type f -path "*third_party/$_lib/*" \
      \! -path "*third_party/$_lib/chromium/*" \
      \! -path "*third_party/$_lib/google/*" \
      \! -path './base/third_party/icu/*' \
      \! -path './third_party/freetype/src/src/psnames/pstables.h' \
      \! -path './third_party/yasm/run_yasm.py' \
      \! -regex '.*\.\(gn\|gni\|isolate\)' \
      -delete
  done

  python2 build/linux/unbundle/replace_gn_files.py \
    --system-libraries "${!_system_libs[@]}"

  msg2 'Applying Chromium launcher patches'
  cd "$srcdir/chromium-launcher-$_launcher_ver"
  patch -Np1 -i ../0020-launcher-branding.patch
}

build() {
  make -C chromium-launcher-$_launcher_ver

  cd "$srcdir/chromium-$pkgver"

  if check_buildoption ccache y; then
    # Avoid falling back to preprocessor mode when sources contain time macros
    export CCACHE_SLOPPINESS=time_macros
  fi

  export PATH="$srcdir/python2-path:$PATH"
  export TMPDIR="$srcdir/temp"
  mkdir -p "$TMPDIR"

  export CC=clang
  export CXX=clang++
  export AR=llvm-ar
  export NM=llvm-nm

  local _flags=(
    'custom_toolchain="//build/toolchain/linux/unbundle:default"'
    'host_toolchain="//build/toolchain/linux/unbundle:default"'
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
    'use_system_freetype=true'
    'use_system_harfbuzz=true'
    'use_gconf=false'
    'use_gnome_keyring=false'
    'use_gold=false'
    'use_sysroot=false'
    'linux_use_bundled_binutils=false'
    'use_custom_libcxx=false'
    'use_system_libjpeg=true'
    'use_system_libpng=true'
    'use_vaapi=true'
    'enable_hangout_services_extension=false'
    'enable_widevine=true'
    'enable_nacl=false'
    'enable_swiftshader=false'
    'enable_nacl_nonsfi=false'
    'enable_remoting=false'
    'enable_google_now=false'
    'enable_reporting=false'
    'safe_browsing_mode=0'
  )

  if check_option strip y; then
    # https://chromium-review.googlesource.com/c/chromium/src/+/712575
    # _flags+=('exclude_unwind_tables=true')
    CFLAGS+='   -fno-unwind-tables -fno-asynchronous-unwind-tables'
    CXXFLAGS+=' -fno-unwind-tables -fno-asynchronous-unwind-tables'
    CPPFLAGS+=' -DNO_UNWIND_TABLES'
  fi

  msg2 'Building GN'
  python2 tools/gn/bootstrap/bootstrap.py -s --no-clean
  msg2 'Configuring Chromium'
  out/Release/gn gen out/Release --args="${_flags[*]}" \
    --script-executable=/usr/bin/python2

  msg2 'Building Chromium'
  ninja -C out/Release chrome chrome_sandbox chromedriver widevinecdmadapter
}

package() {
  cd chromium-launcher-$_launcher_ver
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE.launcher"

  cd "$srcdir/chromium-$pkgver"

  install -D out/Release/chrome "$pkgdir/usr/lib/$pkgname/$pkgname"
  install -Dm4755 out/Release/chrome_sandbox "$pkgdir/usr/lib/$pkgname/chrome-sandbox"
  install -D out/Release/chromedriver "$pkgdir/usr/lib/$pkgname/inoxdriver"
  ln -s /usr/lib/$pkgname/inoxdriver "$pkgdir/usr/bin/inoxdriver"

  install -Dm644 chrome/installer/linux/common/desktop.template \
    "$pkgdir/usr/share/applications/$pkgname.desktop"
  install -Dm644 chrome/app/resources/manpage.1.in \
    "$pkgdir/usr/share/man/man1/$pkgname.1"
  sed -i \
    -e "s/@@MENUNAME@@/${pkgname^}/g" \
    -e "s/@@PACKAGE@@/$pkgname/g" \
    -e "s/@@USR_BIN_SYMLINK_NAME@@/$pkgname/g" \
    "$pkgdir/usr/share/applications/$pkgname.desktop" \
    "$pkgdir/usr/share/man/man1/$pkgname.1"

  cp \
    out/Release/{chrome_{100,200}_percent,resources}.pak \
    out/Release/{*.bin,libwidevinecdmadapter.so} \
    "$pkgdir/usr/lib/$pkgname/"
  install -Dm644 -t "$pkgdir/usr/lib/$pkgname/locales" out/Release/locales/*.pak

  if [[ -z ${_system_libs[icu]+set} ]]; then
    cp out/Release/icudtl.dat "$pkgdir/usr/lib/$pkgname/"
  fi

  for size in 16 22 24 32 48 64 128 256; do
    install -Dm644 "$srcdir/product_logo_$size.png" \
      "$pkgdir/usr/share/icons/hicolor/${size}x${size}/apps/$pkgname.png"
  done

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
