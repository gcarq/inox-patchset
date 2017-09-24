# Maintainer: Michael Egger <gcarq@archlinux.info>
# Contributor: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: Pierre Schmitz <pierre@archlinux.de>
# Contributor: Jan "heftig" Steffens <jan.steffens@gmail.com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

# Build options
_clang=1  # Use Clang instead of GCC for compilation

pkgname=inox
pkgver=61.0.3163.100
pkgrel=1
_launcher_ver=5
pkgdesc="Chromium Spin-off to enhance privacy by disabling data transmission to Google"
arch=('i686' 'x86_64')
url="https://www.chromium.org/Home"
license=('BSD')
depends=('gtk3' 'nss' 'alsa-lib' 'xdg-utils' 'libxss' 'libcups' 'libgcrypt'
         'ttf-font' 'systemd' 'dbus' 'libpulse' 'pciutils' 'json-glib'
         'desktop-file-utils' 'hicolor-icon-theme')
makedepends=('python2' 'gperf' 'yasm' 'mesa' 'ninja' 'nodejs' 'git' 'libva')
(( $_clang )) && makedepends+=('clang' 'lld' 'llvm')
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
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/inox.desktop
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/product_logo_{16,22,24,32,48,64,128,256}.png
        # Patches from Arch Linux
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/breakpad-use-ucontext_t.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-blink-gcc7.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-widevine.patch
        # Patches from Gentoo
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-atk-r1.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-gcc-r1.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-gn-bootstrap-r14.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-mojo-dep.patch
        # Misc
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-libva-remove.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-toolchain.patch
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/chromium-vaapi-r12.patch
        # Inox patchset
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
        https://raw.githubusercontent.com/gcarq/inox-patchset/$pkgver/0021-disable-rlz.patch
        # Custom patches
        9000-disable-metrics.patch
        9001-disable-profiler.patch
        9002-disable-topsites-thumbnails.patch
        9003-disable-avatar-button.patch
        2001-net-cert-increase-default-key-length-for-newly-gener.patch
        2002-prefs-do-not-store-passwords-by-default.patch
        2003-prefs-only-keep-cookies-until-exit.patch
4015-disable-profile-avatar-downloading.patch
4016-disable-signin.patch
4017-disable-translate.patch
4021-fix-building-without-one-click-signin.patch


4003-change-trace-infobar-message.patch
4004-clear-http-auth-cache-menu-item.patch
4005-disable-crash-reporter.patch
4006-disable-domain-reliability.patch
4007-disable-download-quarantine.patch
4008-disable-fonts-googleapis-references.patch
4009-disable-formatting-in-omnibox.patch
4010-disable-gaia.patch
4011-disable-gcm.patch
4012-disable-google-host-detection.patch
4013-disable-intranet-redirect-detector.patch
4014-disable-logging-urls-to-stderr.patch
4015-disable-profile-avatar-downloading.patch
4017-disable-translate.patch
4018-disable-untraceable-urls.patch
4019-disable-webstore-urls.patch
4020-enable-page-saving-on-more-pages.patch
4021-fix-building-without-one-click-signin.patch
4022-fix-learn-doubleclick-hsts.patch
4023-intercept-all-modified-domains.patch
4024-popups-to-tabs.patch
4025-prevent-trace-url-requests.patch
4026-remove-disable-setuid-sandbox-as-bad-flag.patch
4027-remove-get-help-button.patch
4028-replace-google-search-engine-with-nosearch.patch
)

sha256sums=('4135968cac6623c1d2b224494600cd274098cce41c298f8c3908b354a34c281b'
            '4dc3428f2c927955d9ae117f2fb24d098cc6dd67adb760ac9c82b522ec8b0587'
            'ff3f939a8757f482c1c5ba35c2c0f01ee80e2a2273c16238370081564350b148'
            '71471fa4690894420f9e04a2e9a622af620d92ac2714a35f9a4c4e90fa3968dd'
            '4a533acefbbc1567b0d74a1c0903e9179b8c59c1beabe748850795815366e509'
            '7b88830c5e0e9819f514ad68aae885d427541a907e25607e47dee1b0f38975fd'
            '8c10e3b03b13555b461add586422472e0a96d3af49a078d6d952bc0719ba9d94'
            'cc08b771d83b7434c3173c27419bc7d1d4ee375256f3169ef2b9333ba1f2beeb'
            '53a1e8da18069eb4d6ab3af9c923c22a0f020241a4839c3140e3601052ddf6ff'
            '896993987d4ef9f0ac7db454f288117316c2c80ed0b6764019afd760db222dad'
            '3df9b3bbdc07fde63d9e400954dcc6ab6e0e5454f0ef6447570eef0549337354'
            '6e9a345f810d36068ee74ebba4708c70ab30421dad3571b6be5e9db635078ea8'
            'f94310a7ba9b8b777adfb4442bcc0a8f0a3d549b2cf4a156066f8e2e28e2f323'
            'd6fdcb922e5a7fbe15759d39ccc8ea4225821c44d98054ce0f23f9d1f00c9808'
            '45d0e475179a16f614dd90f81be644f1e60f8f7a28c3f3599b583ee59f05963a'
            '11cffe305dd49027c91638261463871e9ecb0ecc6ecc02bfa37b203c5960ab58'
            '98784c4a0a793ecf34987bc8f91ae360d78596a4a59dd47651411381f752a080'
            'fe298059b6937b2816beba8660d42f8584bdc56c12849ac55d32e4cd6d8c4518'
            'c0898cc53ce76f889a8eb107de0e639c2bd4b6d177e385e70ee2ec551b7c17b8'
            '8db6503fbf329fd56cc20d1d1c56ae11bc33247dbb48688a80a9691ca22c9255'
            'f8ec3b1ee04c4830ae6c9c0c9b9d757107430ab52ac0b8d485403bb9a4ef26c7'
            '64ea4bd80788579529e7dac3467c84df74611121041bdd902e6c7dcf8412f3a9'
            '605cca8be9828a29cc96d473847eef9452d572fe6a56dacd96426a202310ba58'
            '3f954d1c101d7ab562c406e3f8c9fe759efffbffec5a65eff09cff6d4ec55cda'
            '98a4b0e3aa54809d05901e231cc6809e471ad4aabadccb5c1c2ca19f94d7dd5f'
            '07710c605df89e9a6548ded7b2c7df2cda5f56441d710f022c947dd35d84e421'
            'bd9194b0a1da60879ce36ac389da6b229be9be5ae6acfba04e3cb0e1cb15ea9f'
            'd22a6f3f6da70e526cbc0917275619ab8f25e260d62e4b350fc7051d7a70a47f'
            'cf050473adae5b83680346b369997b5ead55dce282515f185e4096c5ed39f11d'
            '3190a507dfa00e863a0e622b5738db5cf19947f696ac7a790f427510cc15d1e1'
            '9df082908efe501303b2b0c998b874e5713a0285844dcd170e0e9f435a834277'
            '1d178ac9e0dfa32a5f3dc860cdaa46fdedd7810bc00bc5733f52bdb113be38a6'
            'c79f12e444d2c7b9b61de8d6698033cc8a84bb35f949908b3a366105367237b0'
            '28dddc8a0f59f0ffa5cb3c24b64afb04b3980e34be53c42619978129c8968698'
            '795686bf0dd7bfac0f596155be8fc7ed3f6294a6b764f793cd1614085562ce38'
            '216829c72f1cc378bc66fb4f62f047cccd31684d946ba9a406b6e7a8f1351677'
            'bf1d064fd909ec6a9acc5dd1aeee245bc31eeb90fc3733d9449eb1afe6f262ae'
            '73a9be95e0ec331fb0944b15038000626a43c3bc6f1004b66cc4c29b60fb3fb6'
            'c17556772059a64873ddac383f2976e3befb5c07c3019b641c989ffb5683c4cd'
            '80d2974001708c288a54c24e1dc896ef25916552b740765f6066a244c05ffcd5'
            'dbe942b1eaba525ca6b81d398462a70360fc2043cbfe5d4105657c3bd721e592'
            '8071dfa33d1d17abac81529b910ab006a7535c5edd8868f4244dd33cda6fa251'
            '814fa3b82c8330b944b138ece864be4761fe17f42061816028b5d8c1f2609c8a'
            'd32a51f2d24f0115f29fdcd5f5657c2b0dc39b4a472453bad88861181b005e00'
            '9c07cee733016cda42db01a7f8b25129e0cf9a6640b80cf05bdab56976d8c001'
            '0c0b5fc071d7a92d4b7b7746b6febaef8c76183be7f2bc0a2596dc4d2862829c'
            '9a78e3e58cff87eb64debec2451903d363859ba8c3fbe0c0852a3a685bb0cdc0'
            'f9dc7c5ded54858f0fd4d314df270634a9f7f0b904e00a927da81658aff2262d'
            '502b4eca6edf10fe1d036ab2c65363b4300de91b381ce687e08bd96dc254c898'
            '86b1e2afc0ca261ddbbc4c6a22af165c6cf99505194340b7236afb4896df9d33'
            'b00f417be1befdc651abb521a6656f9864376cc0b40e78c8e6f9fcffe52f8697'
            'cef5dae4b2a7d4cf5ca60d35235594018cfbe3d5c7532f5e64212dd82d39424b'
            'e810acde4a2864a0cae22c13e3031ad59c4236bc2f9940676d861ab8920d2c14'
            'dc5b12678bea3a694a722e3e88277300c4a15050ceb35c9f7d873a5f8ab1ba54'
            '54a1ef701be320915ac271daf26e055c528633667bc7ecdffa2870b4d71f54af'
            'fb3abae54309adf69b98bd2435fbc23f17bc526dbf1d1e97907da87e7cf0aeed'
            'a92129a1d018906a299b9b05c4a96375b115fdd6a3c019d3b326a30a4c107181'
            '21c06cd79dc72a5d007624eaad4f4bc9b17fa25f5fb4ccba84fd34fc2f9500c1'
            'd33c371766dea11dcd2a015d88db34af55c00c8e4064917308337ff6c5386850'
            '1ec1568f0b38f2b828e903e0a13d527afec7758f3d4ef80e0b2b99aee62d9b83'
            '399e1e6dd0d83fc9af2b74817db730661b963e99befc172a1ce0717f869575e6'
            '3e2c52e499809858aa3dd796d9a3fe65bca2a0f681bc430df61ba6bd2592d008'
            '9bf6c2c54ae385b02325fda1782e56d7b9230a2b29e0e8caf84fd1866586c269'
            '55a1c2406ea6ca2219267b48acd3aafa33d4ccf05c455a1bd1d78803e39c13b2'
            '502b4eca6edf10fe1d036ab2c65363b4300de91b381ce687e08bd96dc254c898'
            'b00f417be1befdc651abb521a6656f9864376cc0b40e78c8e6f9fcffe52f8697'
            'd03463b10381f953b5c08f16b99edae22c07d22dbcde3ef5e690c05883a1c5d0'
            '8898a49ef823492fa3086081e649fde37aa3443773c18508707fe2bdf17e15e1'
            '7b2f3813260d81a0f3f27132f9051c3eac27644021795c1dfe0b33d1e4b111c3'
            'cef5dae4b2a7d4cf5ca60d35235594018cfbe3d5c7532f5e64212dd82d39424b'
            '1e917568c707a63df98083f51f14b760a0ff2fb86ac68852cd0690040002295f'
            '1d7b96a95eeb747d1006664cf2e18f62ec0bc31da0e3765fda918c261d34d563'
            'efe4a753739fa9a25c3b72c6f6a49c056df94b9774721b9c9a1cfcf6def8f5c4'
            '55824714159f1614c65f4fda191523ffc39433647b4292e7c2265e35e8755825'
            'bedce54479422789f809c97cc8397696f56f3f60e32559b5b1c1684b7c9df3fa'
            'b2d2c94a0e5db91c0f0007126eaf79313a74361ce320f16fd13d348bd23de1b7'
            'dade96fbca109c9b6be9e6216d87de4e3e5c9203fdd572ed3b6636a34308c3d9')



# Possible replacements are listed in build/linux/unbundle/replace_gn_files.py
# Keys are the names in the above script; values are the dependencies in Arch
declare -rgA _system_libs=(
  #[ffmpeg]=ffmpeg           # https://crbug.com/731766
  [flac]=flac
  #[freetype]=freetype2      # https://crbug.com/pdfium/733
  [harfbuzz-ng]=harfbuzz-icu
  #[icu]=icu                 # https://crbug.com/678661
  [libdrm]=libdrm
  #[libevent]=libevent       # https://bugs.gentoo.org/593458
  [libjpeg]=libjpeg-turbo
  #[libpng]=libpng           # https://crbug.com/752403
  #[libvpx]=libvpx           # https://bugs.gentoo.org/611394
  [libwebp]=libwebp
  [libxml]=libxml2
  [libxslt]=libxslt
  [openh264]=openh264
  #[opus]=opus               # use with system ffmpeg
  [re2]=re2
  [snappy]=snappy
  [yasm]=yasm
  [zlib]=minizip
)
depends+=(${_system_libs[@]})

prepare() {
  msg2 'Warning,  build this program may require near to 3.4 hours, even at an AMD FX 8350 at 4GHz, if you dont have a decent CPU you will wait an eternity,  and if you have a decent cpu  you will wait a long time, please consider it lol'

  cd "$srcdir/chromium-$pkgver"

  msg2 'Patching the sources'
  # Enable support for the Widevine CDM plugin
  # libwidevinecdm.so is not included, but can be copied over from Chrome
  # (Version string doesn't seem to matter so let's go with "Pinkie Pie")
  sed "s/@WIDEVINE_VERSION@/Pinkie Pie/" ../chromium-widevine.patch |
    patch -Np1

  # https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=853347
  patch -Np1 -i ../chromium-blink-gcc7.patch

  # Fix build with glibc 2.26
  patch -Np1 -i ../breakpad-use-ucontext_t.patch

  # Fixes from Gentoo
  patch -Np1 -i ../chromium-atk-r1.patch
  patch -Np1 -i ../chromium-gcc-r1.patch
  patch -Np1 -i ../chromium-gn-bootstrap-r14.patch
  patch -Np1 -i ../chromium-mojo-dep.patch

  # VA-API
  msg2 'Applying VA-API patches'
  patch -Np1 -i ../chromium-libva-remove.patch
  patch -Np1 -i ../chromium-vaapi-r12.patch

  # TODO: remove when the commit arrives in stable
  # https://bugs.gentoo.org/show_bug.cgi?id=587408
  patch -Np1 -i ../chromium-toolchain.patch

  # Make it possible to remove third_party/adobe
  echo > "flapper_version.h"

  msg2 'Applying Inox patchset'
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
  patch -Np1 -i ../0021-disable-rlz.patch

  msg2 'Applying custom patches'
  patch -Np1 -i ../9000-disable-metrics.patch
  patch -Np1 -i ../9001-disable-profiler.patch
  patch -Np1 -i ../9002-disable-topsites-thumbnails.patch
  patch -Np1 -i ../9003-disable-avatar-button.patch



msg2  'Iridium hard'
  #patch -Np1 -i ../2001-net-cert-increase-default-key-length-for-newly-gener.patch
  #patch -Np1 -i ../2002-prefs-do-not-store-passwords-by-default.patch
  patch -Np1 -i ../2003-prefs-only-keep-cookies-until-exit.patch
 
msg2 'UG cute'
  patch -Np1 -i ../4015-disable-profile-avatar-downloading.patch
 
  patch -Np1 -i ../4017-disable-translate.patch
  patch -Np1 -i ../4021-fix-building-without-one-click-signin.patch


msg2 'Edgy'

patch -Np1 -i ../4004-clear-http-auth-cache-menu-item.patch
patch -Np1 -i ../4005-disable-crash-reporter.patch
patch -Np1 -i ../4006-disable-domain-reliability.patch
patch -Np1 -i ../4007-disable-download-quarantine.patch
  patch -Np1 -i ../4008-disable-fonts-googleapis-references.patch
  patch -Np1 -i ../4009-disable-formatting-in-omnibox.patch
  patch -Np1 -i ../4010-disable-gaia.patch
  patch -Np1 -i ../4011-disable-gcm.patch
  patch -Np1 -i ../4012-disable-google-host-detection.patch
  patch -Np1 -i ../4013-disable-intranet-redirect-detector.patch
  patch -Np1 -i ../4018-disable-untraceable-urls.patch
  patch -Np1 -i ../4019-disable-webstore-urls.patch
  patch -Np1 -i ../4020-enable-page-saving-on-more-pages.patch
  patch -Np1 -i ../4022-fix-learn-doubleclick-hsts.patch
  patch -Np1 -i ../4024-popups-to-tabs.patch
  patch -Np1 -i ../4026-remove-disable-setuid-sandbox-as-bad-flag.patch
  patch -Np1 -i ../4027-remove-get-help-button.patch
  
  # Use Python 2
  find . -name '*.py' -exec sed -i -r 's|/usr/bin/python$|&2|g' {} +
  find . -name '*.py' -exec sed -i -r 's|/usr/bin/env python$|&2|g' {} +

  # There are still a lot of relative calls which need a workaround
  mkdir -p "$srcdir/python2-path"
  ln -sf /usr/bin/python2 "$srcdir/python2-path/python"

  # Setup nodejs dependency
  mkdir -p third_party/node/linux/node-linux-x64/bin
  ln -s /usr/bin/node third_party/node/linux/node-linux-x64/bin/

  # Remove bundled libraries for which we will use the system copies; this
  # *should* do what the remove_bundled_libraries.py script does, with the
  # added benefit of not having to list all the remaining libraries
  local _lib
  for _lib in ${!_system_libs[@]}; do
    find -type f \( \
      -path "*base/third_party/$_lib/*" -o \
      -path "*build/secondary/third_party/$_lib/*" -o \
      -path "*third_party/$_lib/*" \) \
      \! -path "*base/third_party/icu/*" \
      \! -path "*third_party/$_lib/chromium/*" \
      \! -path "*third_party/$_lib/google/*" \
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

  # TODO: enable_mdns=false (linker error)
  # TODO: enable_reporting=false (compiler error)
  local _flags=(
    'symbol_level=0'
    'is_debug=false'
    'fatal_linker_warnings=false'
    'treat_warnings_as_errors=false'
    'fieldtrial_testing_like_official_build=true'
    'remove_webcore_debug_symbols=true'
    'exclude_unwind_tables=true'
    'ffmpeg_branding="Chrome"'
    'proprietary_codecs=true'
    'link_pulseaudio=true'
    'use_gconf=false'
    'use_gnome_keyring=false'
    'use_gold=false'
    'use_sysroot=false'
    'linux_use_bundled_binutils=false'
    'use_custom_libcxx=false'
    'use_system_libjpeg=true'
    'use_vaapi=true'
    'enable_hangout_services_extension=false'
    'enable_widevine=true'
    'enable_nacl=false'
    'enable_swiftshader=false'
    'enable_nacl_nonsfi=false'
    'enable_remoting=false'
    'enable_google_now=false'
    'safe_browsing_mode=0'
    'enable_hotwording=false'
    'enable_print_preview=false'
    'enable_webrtc=false'
    'enable_widevine=false'
    'enable_one_click_signin=false'
  )

  # Use the unbundle template to get compiler flags from environment
  # variables like CFLAGS, otherwise they are ignored
  _flags+=('custom_toolchain="//build/toolchain/linux/unbundle:default"'
           'host_toolchain="//build/toolchain/linux/unbundle:default"')

  if (( ! $_clang )); then
    _flags+=('is_clang=false')
    # Set environment variables
    export AR=ar
    export CC=gcc
    export CXX=c++
    export NM=nm
  else
    # Disable Google's Clang plugins and use LLVM's lld linker
    _flags+=('clang_use_chrome_plugins=false'
             'use_lld=true')
    # Set environment variables.
    # '-fno-plt' is default in Arch but officially not supported by Clang
    # and causes an error if used with an unpatched toolchain
    export AR=llvm-ar
    export CC=clang
    export CXX=clang++
    export NM=llvm-nm
    export CFLAGS="${CFLAGS//-fno-plt/} -Wno-unknown-warning-option"
    export CXXFLAGS="${CXXFLAGS//-fno-plt/} -Wno-unknown-warning-option"
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
    out/Release/*.bin \
    out/Release/locales "$pkgdir/usr/lib/$pkgname/"

  if [[ -z ${_system_libs[icu]+set} ]]; then
    cp out/Release/icudtl.dat "$pkgdir/usr/lib/$pkgname/"
  fi

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
