# Maintainer: Gustavo Alvarez <sl1pkn07@gmail.com>
# Contributor: Mikhail Vorozhtsov <mikhail.vorozhtsov@gmail.com>
# Contributor: Nagisa <simonas@kazlauskas.me>
# Contributor: Misc <andreas.reis@gmail.com>
# Contributor: Jeagoss <jgoliver@jeago.com>
# Contributor: Saikrishna Arcot <saiarcot895@gmail.com> and Steven Newbury <steve@snewbury.org.uk> (First Authors of VAAPI patch)

#########################
## -- Build options -- ##
#########################

_use_clang=1     # Use clang compiler (downloaded binaries from google). Results in faster build and smaller chromium.
_use_ccache=0    # Use ccache when build.
_debug_mode=0    # Build in debug mode.

##############################################
## -- Package and components information -- ##
##############################################
pkgname=inox
pkgver=62.0.3202.29
pkgrel=1
pkgdesc="The open-source project behind Google Chrome (Dev Channel)"
arch=('i686' 'x86_64')
url='http://www.chromium.org'
license=('BSD')
depends=(
#          'libsrtp'
         'libxslt'
         'libxss'
         'minizip'
         'nss'
         'pciutils'
         're2'
         'snappy'
         'xdg-utils'
         'libcups'
         'libxml2'
         'harfbuzz-icu'
#          'protobuf'
#          'libevent'
         'ffmpeg'
#          'icu'    # https://crbug.com/678661
         'gtk3'
         'openh264'
         )
makedepends=(
             'libexif'
             'gperf'
             'ninja'
             'python2-beautifulsoup4'
             'python2-html5lib'
             'python2-simplejson'
             'python2-six'
             'subversion'
             'yasm'
             'git'
             'imagemagick'
             'hwids'
             'nodejs'
             'wget'
             )
optdepends=(
            'pepper-flash: PPAPI Flash Player'
            'chromium-widevine-dev: Widevine plugin (eg: Netflix) (Dev Channel)'
            #
            'kdialog: Needed for file dialogs in KF5'
            'kwalletmanager: Needed for storing passwords in KWallet5'
            #
            'ttf-font: For some typography'
            #
            'libappindicator-gtk3: Needed for show systray icon in the panel on GTK3 Desktop based'
            )
source=( #"https://gsdview.appspot.com/chromium-browser-official/chromium-${pkgver}.tar.xz"
        "https://commondatastorage.googleapis.com/chromium-browser-official/chromium-${pkgver}.tar.xz"
        "git+https://github.com/foutrelis/chromium-launcher.git"
        'chromium-dev.svg'
        # Patch form Gentoo
        'https://raw.githubusercontent.com/gentoo/gentoo/master/www-client/chromium/files/chromium-FORTIFY_SOURCE-r2.patch'
        'https://raw.githubusercontent.com/gentoo/gentoo/master/www-client/chromium/files/chromium-gcc5-r2.patch'
        # Misc Patches
        'chromium-intel-vaapi_r14.patch.base64::https://chromium-review.googlesource.com/changes/532294/revisions/d60511c973e432b97d9929dcfbd77c9af25dbd51/patch?download'
        'https://raw.githubusercontent.com/sjnewbury/gentoo-playground/master/www-client/chromium/files/chromium-intel-vaapi-fix.patch'
        # Patch from crbug (chromium bugtracker) or Arch chromium package
        'chromium-gcc-r1.patch::https://git.archlinux.org/svntogit/packages.git/plain/trunk/chromium-gcc-r1.patch?h=packages/chromium'
        'chromium-blink-gcc7-r2.patch' # https://bugs.chromium.org/p/chromium/issues/detail?id=614289
        'chromium-widevine-r1.patch'
        'disable-gns.patch'
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
sha256sums=('c8d4485650ec31144c7e3825de8c7910c94207448df396df1cf4f978a2b01831'
            'SKIP'
            'dd2b5c4191e468972b5ea8ddb4fa2e2fa3c2c94c79fc06645d0efc0e63ce7ee1'
            'fa3f703d599051135c5be24b81dfcb23190bb282db73121337ac76bc9638e8a5'
            'd44b90fc7313afaa6d6f77cde72c0e9a5e4a1cc792216cbca2ed45c39658c472'
            '1974fb5891b6a620113e9527026faa5af771042841ef7b8016ef74e0eaabc926'
            'a688de2b3a7183ebf9eb25108b0d28a8c6228cc71c8e3519062a51224f5b3488'
            '11cffe305dd49027c91638261463871e9ecb0ecc6ecc02bfa37b203c5960ab58'
            'fab4c65e2802e709a32d059784182be5a89bc3ca862a7e27810714ea7b86f868'
            '0d537830944814fe0854f834b5dc41dc5fc2428f77b2ad61d4a5e76b0fe99880'
            'c3fcc27c55956e70608fc73c681c22d0e688b5b2937e803f8bd3b80ceb58c3f7'
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
            '08eb1580239feafb4f8c677b0ad6ba1932787952acf02d139b292c58a2c80851'
            'd6fdcb922e5a7fbe15759d39ccc8ea4225821c44d98054ce0f23f9d1f00c9808'
            '45d0e475179a16f614dd90f81be644f1e60f8f7a28c3f3599b583ee59f05963a'
            '11cffe305dd49027c91638261463871e9ecb0ecc6ecc02bfa37b203c5960ab58'
            '98784c4a0a793ecf34987bc8f91ae360d78596a4a59dd47651411381f752a080'
            'fe298059b6937b2816beba8660d42f8584bdc56c12849ac55d32e4cd6d8c4518'
            'c0898cc53ce76f889a8eb107de0e639c2bd4b6d177e385e70ee2ec551b7c17b8'
            '8db6503fbf329fd56cc20d1d1c56ae11bc33247dbb48688a80a9691ca22c9255'
            'f8ec3b1ee04c4830ae6c9c0c9b9d757107430ab52ac0b8d485403bb9a4ef26c7'
            '993154ba66f0b64558bdf3e6027565200f575638c81b07602330b71012e35f90'
            '605cca8be9828a29cc96d473847eef9452d572fe6a56dacd96426a202310ba58'
            '93aae02be360ebaeb518c9f8a9d276262979423e38b99c0f34a4d4e77c33abea'
            'b7b7db3b1933be54b0a4a9fd67c34d47c463cf8c1f6e00b2becc60ae2722125a'
            'bbdd1992e5568ff63c52c96296e2475e833359c2491749c9bf6e7dc840c6b576'
            'bd9194b0a1da60879ce36ac389da6b229be9be5ae6acfba04e3cb0e1cb15ea9f'
            'd22a6f3f6da70e526cbc0917275619ab8f25e260d62e4b350fc7051d7a70a47f'
            'cf050473adae5b83680346b369997b5ead55dce282515f185e4096c5ed39f11d'
            '3190a507dfa00e863a0e622b5738db5cf19947f696ac7a790f427510cc15d1e1'
            '47505bd7883e99fb966c0a9c225b54f08b12fa953b65e0411e36a994e00204f9'
            '1d178ac9e0dfa32a5f3dc860cdaa46fdedd7810bc00bc5733f52bdb113be38a6'
            'c79f12e444d2c7b9b61de8d6698033cc8a84bb35f949908b3a366105367237b0'
            '28dddc8a0f59f0ffa5cb3c24b64afb04b3980e34be53c42619978129c8968698'
            '795686bf0dd7bfac0f596155be8fc7ed3f6294a6b764f793cd1614085562ce38'
            '216829c72f1cc378bc66fb4f62f047cccd31684d946ba9a406b6e7a8f1351677'
            'bf1d064fd909ec6a9acc5dd1aeee245bc31eeb90fc3733d9449eb1afe6f262ae'
            '68fbca2a2ac5ddb3010418157e6e58c9628218842a518ba118b1c6fb6240bd30'
            'c17556772059a64873ddac383f2976e3befb5c07c3019b641c989ffb5683c4cd'
            '80d2974001708c288a54c24e1dc896ef25916552b740765f6066a244c05ffcd5'
            'dbe942b1eaba525ca6b81d398462a70360fc2043cbfe5d4105657c3bd721e592'
            'aedfaecd40847b72567a0a967f91aec6935139d9f06f2b66c8503ec08380a708'
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
            'fd8f94e205b65d11442409b2ab0d5ee65e07717b73da0efb2e7752d6bdaff23e'
            'a8bae7662aeaa26726c8dcef31fca42a7df516c0984782a2607d2fe462d6c024'
            '1ec1568f0b38f2b828e903e0a13d527afec7758f3d4ef80e0b2b99aee62d9b83'
            '399e1e6dd0d83fc9af2b74817db730661b963e99befc172a1ce0717f869575e6'
            '3e2c52e499809858aa3dd796d9a3fe65bca2a0f681bc430df61ba6bd2592d008'
            '9bf6c2c54ae385b02325fda1782e56d7b9230a2b29e0e8caf84fd1866586c269'
            '55a1c2406ea6ca2219267b48acd3aafa33d4ccf05c455a1bd1d78803e39c13b2'
            '502b4eca6edf10fe1d036ab2c65363b4300de91b381ce687e08bd96dc254c898'
            'b00f417be1befdc651abb521a6656f9864376cc0b40e78c8e6f9fcffe52f8697'
            'd03463b10381f953b5c08f16b99edae22c07d22dbcde3ef5e690c05883a1c5d0'
            '422d3273dcaeab6a8b59f8a483bf8fa997e506d78b7da9062f6563da0c00e2d5'
            '7b2f3813260d81a0f3f27132f9051c3eac27644021795c1dfe0b33d1e4b111c3'
            'cef5dae4b2a7d4cf5ca60d35235594018cfbe3d5c7532f5e64212dd82d39424b'
            '1e917568c707a63df98083f51f14b760a0ff2fb86ac68852cd0690040002295f'
            '1d7b96a95eeb747d1006664cf2e18f62ec0bc31da0e3765fda918c261d34d563'
            'efe4a753739fa9a25c3b72c6f6a49c056df94b9774721b9c9a1cfcf6def8f5c4'
            '55824714159f1614c65f4fda191523ffc39433647b4292e7c2265e35e8755825'
            'bedce54479422789f809c97cc8397696f56f3f60e32559b5b1c1684b7c9df3fa'
            '2365f8f538f8c652e01eeb28fe2fe110a8d50f89d8c565931e0af9c1b659587d'
            'dade96fbca109c9b6be9e6216d87de4e3e5c9203fdd572ed3b6636a34308c3d9')
options=('!strip')
install=chromium-dev.install

################################################
## -- Don't touch anything below this line -- ##
################################################

# Build Debug mode?.
if [ "${_debug_mode}" = "1" ]; then
  _debug_flag="symbol_level=1"
  _strip=false
elif [ "${_debug_mode}" = "0" ]; then
  _strip=true
fi

# Google API keys (see http://www.chromium.org/developers/how-tos/api-keys)
# NOTE: These are for Arch Linux use ONLY. For your own distribution, please
# get your own set of keys. Feel free to contact foutrelis@archlinux.org for
# more information.
_google_api_key="AIzaSyDwr302FpOSkGRpLlUpPThNTDPbXcIn_FM"
_google_default_client_id="413772536636.apps.googleusercontent.com"
_google_default_client_secret="0ZChLK6AxeA3Isu96MkwqDR4"

# Build NaCL?. disabled if detect 32bit system
# VULKAN!! (seems only build with 64 bits) # https://crbug.com/582558 NOTE: disabled by default
if [ "${CARCH}" = "i686" ]; then
  _build_nacl=0
  _nacl="false"
elif [ "${CARCH}" = "x86_64" ]; then
  _build_nacl=1
  _nacl="true"
  #_vulkan=1
  makedepends+=('ncurses5-compat-libs')
fi

# Need you use ccache?.
if [ "${_use_ccache}" = "1" ]; then
  makedepends+=('ccache')
fi

# Are you use gnome-keyring/gnome?.
_gnome_keyring=false
if [ -e /usr/lib/libgnome-keyring.so.0 ]; then
  depends+=('libgnome-keyring')
  _gnome_keyring=true
fi

# List of third-party components needed for build chromium. The rest is remove by remove_bundled_libraries srcipt in prepare().
_keeplibs=(
           'base/third_party/dmg_fp'
           'base/trace_event'
           'base/third_party/dynamic_annotations'
           'base/third_party/icu'
           'base/third_party/nspr'
           'base/third_party/superfasthash'
           'base/third_party/symbolize'
           'base/third_party/valgrind'
           'base/third_party/xdg_mime'
           'base/third_party/xdg_user_dirs'
           'breakpad/src/third_party/curl'
           'chrome/third_party/mozilla_security_manager'
           'courgette/third_party'
           'native_client/src/third_party/dlmalloc'
           'native_client_sdk/src/libraries/third_party/newlib-extras'
           'net/third_party/mozilla_security_manager'
           'net/third_party/nss'
           'third_party/WebKit'
           'third_party/analytics'
           'third_party/angle'
           'third_party/angle/src/common/third_party/base'
           'third_party/angle/src/common/third_party/murmurhash'
           'third_party/angle/src/third_party/compiler'
           'third_party/angle/src/third_party/libXNVCtrl'
           'third_party/angle/src/third_party/trace_event'
           'third_party/blink'
           'third_party/boringssl'
           'third_party/brotli'
           'third_party/cacheinvalidation'
           'third_party/catapult'
           'third_party/catapult/third_party/polymer'
           'third_party/catapult/third_party/py_vulcanize'
           'third_party/catapult/third_party/py_vulcanize/third_party/rcssmin'
           'third_party/catapult/third_party/py_vulcanize/third_party/rjsmin'
           'third_party/catapult/tracing/third_party/d3'
           'third_party/catapult/tracing/third_party/gl-matrix'
           'third_party/catapult/tracing/third_party/jszip'
           'third_party/catapult/tracing/third_party/mannwhitneyu'
           'third_party/catapult/tracing/third_party/oboe'
           'third_party/ced'
           'third_party/cld_2'
           'third_party/cld_3'
           'third_party/crc32c'
           'third_party/cros_system_api'
           'third_party/devscripts'
           'third_party/dom_distiller_js'
           'third_party/fips181'
           'third_party/flatbuffers'
           'third_party/flot'
           'third_party/freetype'
           'third_party/glslang-angle'
           'third_party/google_input_tools'
           'third_party/google_input_tools/third_party/closure_library'
           'third_party/google_input_tools/third_party/closure_library/third_party/closure'
           'third_party/googletest'
           'third_party/hunspell'
           'third_party/iccjpeg'
           'third_party/inspector_protocol'
           'third_party/jinja2'
           'third_party/jstemplate'
           'third_party/khronos'
           'third_party/leveldatabase'
           'third_party/libXNVCtrl'
           'third_party/libaddressinput'
           'third_party/libjingle'
           'third_party/libphonenumber'
           'third_party/libsecret'
           'third_party/libsrtp'
           'third_party/libudev'
           'third_party/libvpx'
           'third_party/libvpx/source/libvpx/third_party/x86inc'
           'third_party/libwebm'
           'third_party/libxml/chromium'
           'third_party/libyuv'
           'third_party/lss'
           'third_party/lzma_sdk'
           'third_party/markupsafe'
           'third_party/mesa'
           'third_party/modp_b64'
           'third_party/mt19937ar'
           'third_party/node'
           'third_party/node/node_modules/polymer-bundler/lib/third_party/UglifyJS2'
           'third_party/openmax_dl'
           'third_party/ots'
           'third_party/pdfium'
           'third_party/pdfium/third_party/agg23'
           'third_party/pdfium/third_party/base'
           'third_party/pdfium/third_party/build'
           'third_party/pdfium/third_party/bigint'
           'third_party/pdfium/third_party/freetype'
           'third_party/pdfium/third_party/lcms'
           'third_party/pdfium/third_party/libopenjpeg20'
           'third_party/pdfium/third_party/libpng16'
           'third_party/pdfium/third_party/libtiff'
           'third_party/ply'
           'third_party/polymer'
           'third_party/protobuf'
           'third_party/protobuf/third_party/six'
           'third_party/qcms'
           'third_party/sfntly'
           'third_party/skia'
           'third_party/skia/third_party/gif'
           'third_party/skia/third_party/vulkan'
           'third_party/smhasher'
           'third_party/spirv-headers'
           'third_party/spirv-tools-angle'
           'third_party/sqlite'
           'third_party/swiftshader'
           'third_party/swiftshader/third_party/llvm-subzero'
           'third_party/swiftshader/third_party/subzero'
           'third_party/tcmalloc'
           'third_party/usrsctp'
           'third_party/vulkan-validation-layers'
           'third_party/vulkan'
           'third_party/web-animations-js'
           'third_party/webdriver'
           'third_party/webrtc'
           'third_party/widevine'
           'third_party/woff2'
           'third_party/zlib/google'
           'url/third_party/mozilla'
           'v8/src/third_party/valgrind'
           'v8/third_party/inspector_protocol'

           # gyp -> gn leftovers
           'base/third_party/libevent'
           'third_party/adobe'
           'third_party/speech-dispatcher'
           'third_party/usb_ids'
           'third_party/xdg-utils'
           'third_party/yasm/run_yasm.py'
           )

# Set build flags.
_flags=(
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
    'remove_webcore_debug_symbols=true'
        )

if [ "$_vulkan" = "1" ]; then
  _flags+=('enable_vulkan=true')
  _keeplibs+=(
              'third_party/SPIRV-Tools'
              'third_party/glslang'
              'third_party/shaderc'
              )
fi

# Enable VAAPI, see https://chromium-review.googlesource.com/532294
_flags+=('use_vaapi=true')
optdepends+=(
             'libva-vdpau-driver-chromium: HW video acceleration for NVIDIA users'
             'libva-mesa-driver: HW video acceleration for Nouveau, R600 and RadeonSI users'
             'libva-intel-driver: HW video acceleration for Intel G45 and HD users'
            )

# Set the bundled/external components.
# TODO: need ported to GN as GYP doing before. see status page: https://crbug.com/551343
_use_system=(
             'ffmpeg'
             'flac'
#             'freetype'   # https://bugs.chromium.org/p/pdfium/issues/detail?id=733
             'harfbuzz-ng'
#             'icu'        # https://crbug.com/678661
             'libdrm'
#             'libevent'   # Get segfaults and other problems https://bugs.gentoo.org/593458
             'libjpeg'
             'libpng'
#             'libsrtp'    # https://bugs.gentoo.org/459932
#             'libvpx'     # Needs update
             'libwebp'
             'libxml'
             'libxslt'
             'openh264'
             'opus'
             're2'
             'snappy'
             'yasm'
             'zlib'
             )

# Conditionals.
if [ "${_debug_mode}" = "1" ]; then
  _keeplibs+=('native_client/src/third_party/valgrind')
fi

# https://crbug.com/678661
if [ "${_build_nacl}" = "1" ]; then
  _keeplibs+=('third_party/icu') # https://crbug.com/678661
elif [ "${_build_nacl}" = "0" ]; then
  depends+=('icu')
  _use_system+=('icu')
fi

################################################

prepare() {
  # Use custom toolchain.
  _flags+=(
           "custom_toolchain=\"//build/toolchain/linux/unbundle:default\""
           "host_toolchain=\"//build/toolchain/linux/unbundle:default\""
           )

  # Set Python2 path.
  mkdir -p python-path
  ln -sf /usr/bin/python2 "${srcdir}/python-path/python"
  export PATH="${srcdir}/python-path:$PATH"

  cd "$srcdir/chromium-launcher"
  patch -Np1 -i ../0020-launcher-branding.patch

  cd "${srcdir}/chromium-${pkgver}"

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
  


  msg2 "Patching the sources"
  # Patch sources from Gentoo.
  patch -p1 -i "${srcdir}/chromium-FORTIFY_SOURCE-r2.patch"
  # Fix build with gcc 7(?)
  patch -p1 -i "${srcdir}/chromium-gcc5-r2.patch"
  # Pats to chromium dev's about why always they forget add/remove missing build rules
   patch -p1 -i "${srcdir}/disable-gns.patch"
  # Misc Patches:

  if [ "${_vulkan}" = "1" ]; then
    export VULKAN_SDK="/usr"
    sed 's|base/||' -i cc/output/vulkan_renderer.h
    sed 's|/x86_64-linux-gnu||' -i gpu/vulkan/BUILD.gn
  fi

  # Apply VAAPI patch
  base64 -d "${srcdir}/chromium-intel-vaapi_r14.patch.base64" > chromium-intel-vaapi_r14.patch
  sed '39,50d' -i chromium-intel-vaapi_r14.patch
  patch -Np1 -i chromium-intel-vaapi_r14.patch
  patch -p1 -i "${srcdir}/chromium-intel-vaapi-fix.patch"

  # Patch from crbug (chromium bugtracker) or Arch chromium package

  # Fix build with gcc 7(?)
  patch -p1 -i "${srcdir}/chromium-gcc-r1.patch"
  patch -p1 -i "${srcdir}/chromium-blink-gcc7-r2.patch"

  # https://crbug.com/473866
  patch -p0 -i "${srcdir}/chromium-widevine-r1.patch"
  sed 's|@WIDEVINE_VERSION@|The Cake Is a Lie|g' -i "third_party/widevine/cdm/stub/widevine_cdm_version.h"

  # Setup nodejs dependency
  mkdir -p third_party/node/linux/node-linux-x64/bin/
  ln -sf /usr/bin/node third_party/node/linux/node-linux-x64/bin/node

  # Try to fix libpng errors.
  msg2 "Attempt for fix libpng errors"
  for _path in 'chrome/app/theme' 'chrome/renderer' 'ui'; do
    pushd "${_path}" &> /dev/null
    export IFS=$'\n'
    for i in $(find . -name '*.png' -type f); do
      mogrify "${i}" &> /dev/null
    done
    export IFS=' '
    popd &> /dev/null
  done

  # Remove most bundled libraries. Some are still needed.
  msg2 "Removing unnecessary components to save space."
  python2 build/linux/unbundle/remove_bundled_libraries.py ${_keeplibs[@]} --do-remove

  msg2 "Make sure use Python2"
  find -name '*.py' | xargs sed -e 's|env python|&2|g' -e 's|bin/python|&2|g' -i

  msg2 "Changing bundle libraries to system ones."
  python2 build/linux/unbundle/replace_gn_files.py --system-libraries ${_use_system[@]}

  # Use the file at run time instead of effectively compiling it in.
  sed 's|//third_party/usb_ids/usb.ids|/usr/share/hwdata/usb.ids|g' -i device/usb/BUILD.gn

  if [ "${_build_nacl}" = "1" ]; then
    msg2 "Setup NaCl/PNaCl SDK: Download and install NaCl/PNaCl toolchains"
    python2 build/download_nacl_toolchains.py --packages nacl_x86_newlib,pnacl_newlib,pnacl_translator sync --extract
    # Download clang from google. need for build NaCl. also is used by build the project in x86_64 systems when use clang
    python2 tools/clang/scripts/update.py
  fi

  # Setup compilers.
  if [ "${_use_ccache}" = "1" ]; then
    export CCACHE_CPP2=yes
    export CCACHE_SLOPPINESS=time_macros
    _ccache='ccache'
    _ccache_flags='-Qunused-arguments'
  fi

  _set_gcc() {
    _compiler=GCC
    _flags+=(
             'is_clang=false'
             'clang_use_chrome_plugins=false'
             )
    _c_compiler="gcc"
    _cpp_compiler="g++"
    CFLAGS+=" -fno-delete-null-pointer-checks"
    CXXFLAGS+=" -fno-delete-null-pointer-checks"
  }

  if [ "${_use_clang}" = "0" ]; then
    _set_gcc
  elif [ "${_use_clang}" = "1" ]; then
    if [ "${CARCH}" = 'i686' ]; then
      _set_gcc
      _compiler_msg=": Build with (bundled) clang is not possible in 32bit systems."
    elif [ "${CARCH}" = 'x86_64' ]; then
      _compiler=Clang
      _flags+=(
               'is_clang=true'
               'clang_use_chrome_plugins=true'
              )
      _clang_path="${srcdir}/chromium-${pkgver}/third_party/llvm-build/Release+Asserts/bin"
      _c_compiler="${_clang_path}/clang"
      _cpp_compiler="${_clang_path}/clang++"
      export CXXFLAGS="${CXXFLAGS//-fno-plt/}"
      export CFLAGS="${CFLAGS//-fno-plt/}"
      CFLAGS+=' -Wno-unknown-warning-option'
      CXXFLAGS+=' -Wno-unknown-warning-option'
    fi
  fi

  # Export compilers
  msg2 "Setup ${_compiler} compiler${_compiler_msg}"
  export AR=ar
  export NM=nm
  export CC="${_ccache} ${_c_compiler} ${_ccache_flags}"
  export CXX="${_ccache} ${_cpp_compiler} ${_ccache_flags}"
}

build() {

  msg2 "Build the Launcher"
  make -C "chromium-launcher" \
     CHROMIUM_SUFFIX="-dev" \

  cd "chromium-${pkgver}"

  msg2 "Starting building Chromium..."
  # Configure the builder.
  python2 tools/gn/bootstrap/bootstrap.py -v -s --no-clean
  out/Release/gn gen out/Release -v --args="${_flags[*]} ${_debug_flag}" --script-executable=/usr/bin/python2

  msg2 'kek'
  LC_ALL=C ninja -C out/Release -v pdf chrome chrome_sandbox chromedriver widevinecdmadapter clearkeycdm
}

package() {
  # Install launcher.
  make -C "chromium-launcher" \
    PREFIX=/usr \
    CHROMIUM_SUFFIX="-dev" \
    DESTDIR="${pkgdir}" \
    install
  install -Dm644 "chromium-launcher/LICENSE" "${pkgdir}/usr/share/licenses/inox/LICENSE.launcher"

  pushd "chromium-${pkgver}/out/Release" &> /dev/null

  # Build with debug needs a tons of space. remove this save that space, but break the rebuild process.
  if [ "${_debug_mode}" = "1" ]; then
    rm -fr "chromium-${pkgver}/third_party"
  fi

  # Install binaries.
  install -Dm755 chrome "${pkgdir}/usr/lib/inox/inox"
  install -Dm644 chrome.1 "${pkgdir}/usr/share/man/man1/inox.1"
  install -Dm4755 chrome_sandbox "${pkgdir}/usr/lib/inox/chrome-sandbox"
  install -Dm755 chromedriver "${pkgdir}/usr/lib/inox/inoxdriver"
  ln -sf /usr/lib/inox/inoxdriver "${pkgdir}/usr/bin/inoxdriver"

  # Install libs.
  _libs=(
         'libclearkeycdm.so'
         'libEGL.so'
         'libGLESv2.so'
         'libVkLayer_core_validation.so'
         'libVkLayer_object_tracker.so'
         'libVkLayer_parameter_validation.so'
         'libVkLayer_swapchain.so'
         'libVkLayer_threading.so'
         'libVkLayer_unique_objects.so'
         'libwidevinecdmadapter.so'
         'swiftshader/libEGL.so'
         'swiftshader/libGLESv2.so'
         #
         'natives_blob.bin'
         'snapshot_blob.bin'
         )
  for i in "${_libs[@]}"; do
    install -Dm755 "${i}" "${pkgdir}/usr/lib/inox/${i}"
  done

  # Install Resources.
  _resources=(
              'chrome_100_percent.pak'
              'chrome_200_percent.pak'
              'headless_lib.pak'
              'keyboard_resources.pak'
              'mus_app_resources_100.pak'
              'mus_app_resources_200.pak'
              'mus_app_resources_strings.pak'
              'resources.pak'
              'views_mus_resources.pak'
              )
  for i in "${_resources[@]}"; do
    install -Dm644 "${i}" "${pkgdir}/usr/lib/inox/${i}"
  done
  find resources -type f -name "*" -exec install -Dm644 '{}' "${pkgdir}/usr/lib/inox/{}" \;

  # Install locales.
  find locales -type f -name "*.pak" -exec install -Dm644 '{}' "${pkgdir}/usr/lib/inox/{}" \;

  # Install icons.
  for _size in 16 22 24 32 48 128 256; do
    case "${_size}" in
      16|32) _branding="${srcdir}/chromium-${pkgver}/chrome/app/theme/default_100_percent/chromium" ;;
      *) _branding="${srcdir}/chromium-${pkgver}/chrome/app/theme/chromium" ;;
    esac
    install -Dm644 "${_branding}/product_logo_${_size}.png" "${pkgdir}/usr/share/icons/hicolor/${_size}x${_size}/apps/chromium-dev.png"
  done
  install -Dm644 "${srcdir}/chromium-dev.svg" "${pkgdir}/usr/share/icons/hicolor/scalable/apps/chromium-dev.svg"

  for size in 16 22 24 32 48 64 128 256; do
    install -Dm644 "$srcdir/product_logo_$size.png" \
      "$pkgdir/usr/share/icons/hicolor/${size}x${size}/apps/$pkgname.png"
  done

  # Install NaCL stuff if is detected.
  if [ "${_build_nacl}" = "1" ]; then
    _nacl_libs=(
                'nacl_helper'
                'nacl_helper_bootstrap'
                'nacl_helper_nonsfi'
                'nacl_irt_x86_64.nexe'
                'icudtl.dat'
                )
    for i in "${_nacl_libs[@]}"; do
      install -Dm755 "${i}" "${pkgdir}/usr/lib/inox/${i}"
    done
  fi

  popd &> /dev/null

 install -Dm644 "$srcdir/$pkgname.desktop" \
    "$pkgdir/usr/share/applications/$pkgname.desktop"

  # Install some external files.
  install -Dm644 "chromium-${pkgver}/chrome/installer/linux/common/desktop.template" "${pkgdir}/usr/share/applications/chromium-dev.desktop"
  sed -e 's|@@MENUNAME@@|Chromium-dev|g' \
      -e 's|@@USR_BIN_SYMLINK_NAME@@|chromium-dev|g' \
      -e 's|@@PACKAGE@@|chromium-dev|g' \
      -i "${pkgdir}/usr/share/applications/chromium-dev.desktop"
  install -Dm644 "chromium-${pkgver}/LICENSE" "${pkgdir}/usr/share/licenses/inox/LICENSE"

  if [ "${_debug_mode}" = "0" ]; then
    # Manually strip binaries so that 'nacl_irt_*.nexe' is left intact.
    if [ "${_build_nacl}" = "1" ]; then
      strip $STRIP_BINARIES "${pkgdir}/usr/lib/inox/"nacl_helper{,_bootstrap,_nonsfi}
    fi
    strip $STRIP_BINARIES "${pkgdir}/usr/lib/inox/"{inox,chrome-sandbox,inoxdriver}
    strip $STRIP_SHARED "${pkgdir}/usr/lib/inox/"lib*.so
    strip $STRIP_SHARED "${pkgdir}/usr/lib/inox/swiftshader/"lib*.so
  fi

  # Try to fix libpng errors. (second attemp)
  for _path in "${pkgdir}/usr/lib/inox/resources/inspector/Images"; do
    pushd "${_path}" &> /dev/null
    export IFS=$'\n'
    for i in $(find . -name '*.png' -type f); do
      mogrify "${i}" &> /dev/null
    done
    export IFS=' '
    popd &> /dev/null
  done
}
