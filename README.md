# Inox Browser (inox-patchset)

Inox patchset is applied on the chromium source code and tries to prevent data transmission to Google to get a minimal Chromium based browser. The patches are split up based on features, so it's easy to patch only a subset of them.

Table of Contents
* [Foreword](#foreword)
* [Download](#download)
* [Building](#building)
    * [Patches](#patches)
    * [Build flags](#build-flags)
* [Frequently-asked questions](#frequently-asked-questions)
    * [Install extensions from Google WebStore](#install-extensions-from-google-webstore)
    * [Use widevine](#use-widevine)
    * [Use a proxy](#use-a-proxy)
    * [Use firejail](#use-firejail)
    * [Reduce memory footprint](#reduce-memory-footprint)
* [Screenshots](#screenshots)
* [Contributing](#contributing)
* [Credits](#credits)
* [License](#license)
* [Donations](#donations)


## Foreword
It is possible that some data is still transmitted (but down to a minimum) this is because Chromium is a quite large and complex codebase which changes each day.

## Download
* **Arch Linux**:
Pre-built binaries are hosted in the AUR: [inox-bin](https://aur.archlinux.org/packages/inox-bin/)

* **Ubuntu, Debian, OSX, Windows**: See [ungoogled-chromium](https://github.com/Eloston/ungoogled-chromium), it offers pre-built binaries with inox-patchset and various other patches.

## Building
These patches are tested and functional on Arch Linux x86_64, but should run on any Linux/BSD distribution.

*The build process takes about 3 hours on a i5-3550 CPU @ 3.90GHz and 16GB ram. (without ccache)*

* **Arch Linux**:
If you are running Arch Linux you can download and build the source from AUR: [inox](https://aur.archlinux.org/packages/inox/)

* **Ubuntu, Debian, OSX, Windows**: See [ungoogled-chromium](https://github.com/Eloston/ungoogled-chromium), it offers build scripts to compile Chromium with inox-patchset and various other patches.

* **Build manually:** If you want to build it yourself check out the Chromium [Build Instructions](https://chromium.googlesource.com/chromium/src/+/master/docs/linux_build_instructions.md) or view the [PKGBUILD](https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=inox) to get an idea how chromium is built.


### Patches

##### restore-classic-ntp.patch
Restores old NTP (New Tab Page).
The default NTP loads data from a web server to modify the appearance and inject a Google Search bar with a unique identifier.


##### add-duckduckgo-search-engine.patch
Adds DuckDuckGo as default search engine, it's still changeable in settings.


##### disable-default-extensions.patch
Enabled user-modification for all extensions.
Disabled extensions:
* Hotword (incl. Shared Module)
* Google Now
* Google Feedback
* Cloud Print
* Google Webstore
* Network Speech synthesis
* Google Hangout


##### disable-autofill-download-manager.patch
Disables HTML-Form AutoFill data transmission. I don't know exactly when this is triggered, but it synchronizes the saved Form data with Google.


##### disable-google-url-tracker.patch
Disables URLTracker, which checks in which country you are to provide the closest google server for search lookups.
I know this class has a bad naming, but nevertheless it connects to Google.


##### disable-google-ipv6-probes.patch
Disables ipv6 probes to Google servers.
Google pings its own DNS server to check if ipv6 is available. Changed this to RIPE NCC k.root-servers.net. 2001:7fd::1 (anycasted).


##### disable-gcm-status-check.patch
Disables Google Cloud-Messaging status probes. GCM provides an interface to send messages directly to single devices, groups of devices, or devices subscribed to topics.


##### disable-missing-key-warning.patch
Disables warning dialog about missing Google API key.
This key is usually set on compile time and unique per distribution.
See [ArchLinux chromium PKGBUILD](https://projects.archlinux.org/svntogit/packages.git/tree/trunk/PKGBUILD?h=packages/chromium#n37) on how it's applied or this [HOWTO](https://www.chromium.org/developers/how-tos/api-keys) for an in-depth API key explanation.

Since we don't want to use these APIs at all, the keys are not set (at least for inox package on AUR).


##### disable-translation-lang-fetch.patch
* Disables language fetching when settings are opened for the first time
* Disables TranslateRankerQuery and TranslateRankerEnforcement (connects to `chromium-i18n.appspot.com`)

##### disable-update-pings.patch
Disables update pings to `https://clients2.google.com/service/update2` which is used for component updates.


##### chromium-sandbox-pie.patch
Hardening the sandbox with Position Independent Code(PIE) against ROP exploits.
This patch is originally from openSUSE.


##### disable-new-avatar-menu.patch
Disables Google's new Avatar and signin menu.


##### disable-first-run-behaviour.patch
Modifies the first-run behaviour to prevent data leakage.


##### disable-battery-status-service.patch
The W3C Battery Status API[1] has quite a laughable statement:

"The information disclosed has minimal impact on privacy or
fingerprinting, and therefore is exposed without permission grants".

Along comes a paper "The leaking battery, A privacy analysis of the
HTML5 Battery Status API."

Clean up after the W3C and disable the battery status updater which
could be used to identity users[2].

* [1] http://www.w3.org/TR/battery-status/
* [2] https://eprint.iacr.org/2015/616.pdf

References: https://github.com/iridium-browser/iridium-browser/issues/40


##### modify-default-prefs.patch

Modifies following default settings (can be changed anytime):

User setting | new value
--- | ---
DefaultCookiesSettings     | `CONTENT_SETTING_DEFAULT`
EnableHyperLinkAuditing    | `false`
CloudPrintSubmitEnabled    | `false`
NetworkPredictionEnabled   | `false`
BackgroundModeEnabled      | `false`
BlockThirdPartyCookies     | `true`
AlternateErrorPagesEnabled | `false`
SearchSuggestEnabled       | `false`
AutofillEnabled            | `false`
Send feedback to Google if preferences are reset | `false`
BuiltInDnsClientEnabled    | `false`
SignInPromoUserSkipped     | `true`
SignInPromoShowOnFirstRunAllowed | `false`
ShowAppsShortcutInBookmarkBar | `false`
ShowBookmarkBar | `true`
PromptForDownload | `true`
SafeBrowsingEnabled | `false`
EnableTranslate | `false`
LocalDiscoveryNotificationsEnabled | `false`


##### branding.patch
`s/Chromium/Inox/g`


### Build flags
The PKGBUILD uses chromium [GN build system](https://chromium.googlesource.com/chromium/src/tools/gn/).
The following config flags are applied:

Feature | Build config
--- | ---
Disable google now |                `enable_google_now=false`
Disable WebRTC |                    `enable_webrtc=false`
Disable Remote service |          `enable_remoting=false`
Disable safe browsing |             `safe_browsing_mode=0*`
Disable RLZ Identifier |              `enable_rlz=false`, `enable_rlz_support=false`
Disable google hangouts |         `enable_hangout_services_extension=false`
Disable print preview |                `enable_print_preview=false`

\* Builds only with `fix-building-without-safebrowsing.patch`.


## Frequently-asked questions

### Install extensions from Google WebStore


Since there is no WebStore plugin, you cannot install extensions directly from the store, but there are two options to install an extension.

**Keep in mind extensions are not updated automatically, so make sure you update them on a regular base.**

* **Extension downloader**

   The most convenient way is via the extension downloader [inoxunpack](https://github.com/gcarq/inoxunpack), it's a small python script to download and unpack extensions from Google WebStore.

   Example usages:
   ```
   $ inoxunpack ublock-origin
   $ inoxunpack cjpalhdlnbpafiamejdnhcphjbkeiagm
   ```
   Both of the commands will download but not install ublock origin. After executing you will se an instruction how to install the extension in developer mode. See inoxunpack for more details.

* **Download manually**

  `https://clients2.google.com/service/update2/crx?response=redirect&os=linux&prodversion=55.0.2883.87&x=id%3D[EXTENSION_ID]%26installsource%3Dondemand%26uc`

   To download a extension just replace `[EXTENSION_ID]` with the extension-id from the WebStore (For example `cjpalhdlnbpafiamejdnhcphjbkeiagm` is the extension id of uBlock Origin).

   **Drag and Drop**

   Open `chrome://extensions` and drop the file from the download bar into the extensions tab. **Note:** Under some circumstances this method does not work on KDE Plasma.

   **Preferences File**

   Alternatively you can also install the extension via a preferences file.

   For example to install the extension cjpalhdlnbpafiamejdnhcphjbkeiagm create a file called: `/usr/share/inox/extensions/cjpalhdlnbpafiamejdnhcphjbkeagm.json` with following content:
   ```json
   {
       "external_crx": "/path/to/extension/extension_1_0_0.crx",
       "external_version": "1.0.0"
   }
   ```
   If you restart Inox the extension should be loaded automatically. For more details go [here](https://developer.chrome.com/extensions/external_extensions#preferences).

### Use widevine
Though it might not be ideal to use DRM technologies, Inox supports widevine if you provide `libwidevinecdm.so`.
To activate it, create a symlink from a chromium setup.

`# ln -s /usr/lib/chromium/libwidevinecdm.so /usr/lib/inox/libwidevinecdm.so`

### Use a proxy
As mentioned in [Foreword](#foreword) it is still possible that some data is leaked to Google, so use if want to use a proxy to achieve a high level of anonymity it would be better to use TorBrowser.

The `--proxy-server` flag supports `HTTP`, `HTTPS` and `SOCKS` proxies.
The `--host-resolver-rules` flag forces DNS requests through the proxy (prevents DNS leakage), the `EXCLUDE` option lets Inox resolve the domain name.

#### Examples

###### Tor
`inox --proxy-server="socks5://localhost:9050" --host-resolver-rules="MAP * 0.0.0.0, EXCLUDE localhost, EXCLUDE *.local"`

###### I2P
`inox --proxy-server="http://127.0.0.1:4444" --host-resolver-rules="MAP * 0.0.0.0, EXCLUDE localhost, EXCLUDE *.local"`

### Use firejail
[Firejail](https://github.com/netblue30/firejail) is a SUID program that reduces the risk of security breaches by restricting the running environment of untrusted applications using Linux namespaces and seccomp-bpf.
It supports Inox out of the box, you just need to run inox with firejail: `firejail inox`.

### Reduce memory footprint
#### Enabling process per site
By default Chrom* heavily isolates each tab regardless of it's domain. While doing this arguably improves security by some extent, downside is that as number of tabs increase, the RAM bloat due to duplication reaches absurd levels. This can end up with Chrom* using >4.5GB of RAM on a machine with 8GB thus preventing other heavy programs from running at the same time. This can be fixed by making Chrom* use one process per site/domain and not per tab. This greatly reduces RAM bloat while (probably) not sacrificing much from security. Use the following command-line argument:
`inox --process-per-site`

For more details go [here](https://www.chromium.org/developers/design-documents/process-models).

## Screenshots
![Inox Browser](http://i.imgur.com/eNiCycy.png "Inox Browser")

[Here](http://imgur.com/a/IUfqm) you can find more screenshots.


## Contributing
Use the Issue Tracker for problems, suggestions, and questions, or visit the [Inox Browser thread](https://bbs.archlinux.org/viewtopic.php?id=198763) in the Arch forums.

You may also contribute by submitting pull requests.


## Credits
* [Chromium](https://www.chromium.org/)
* [Iridium Browser](https://iridiumbrowser.de/)
* [ungoogled-chromium](https://github.com/Eloston/ungoogled-chromium)


## License
GPLv3. See [LICENSE](LICENSE)

## Donations
Donations are welcome and keep me motivated :-)
* BTC: `1EsahKzwNgZF56gmZZz8NVQJ4SWdGnshv4`
