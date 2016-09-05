# inox-patchset
Inox patchset is applied on the chromium source code and tries to prevent data transmission to Google to get a minimal Chromium based browser. The patches are split up based on features, so it's easy to patch only a subset of them.
See below for a full list of patched features. Some of them are also disabled via build flags.

Here you can find some screenshots: http://imgur.com/a/IUfqm






## Warning
It is possible that some data is still transmitted(but down to a minimum) this is because Chromium is a quite large and complex codebase which changes each day.


## Building
These patches are tested and functional on Arch Linux x86_64, but should run on any Linux/BSD distribution.
If you are running Arch Linux you can download the source or binary package from AUR:
* [inox](https://aur.archlinux.org/packages/inox/)
* [inox-bin](https://aur.archlinux.org/packages/inox-bin/)

For debian based distributions see [ungoogled-chromium](https://github.com/Eloston/ungoogled-chromium), it offers a debian build script to compile Chromium with various patches and also a pre-built version.

For any other distribution check out the Chromium [Build Instructions](https://chromium.googlesource.com/chromium/src/+/master/docs/linux_build_instructions.md) or view the inox [PKGBUILD](https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=inox) to get an idea how chromium is built.

*The build process takes about 3 hours on a i5-3550 CPU @ 3.90GHz and 16GB ram. (without ccache)*


## Patches

#### restore-classic-ntp.patch
Restores old NTP (New Tab Page).
The default NTP loads data from a web server to modify the appearance and inject a Google Search bar with a unique identifier.


#### add-duckduckgo-search-engine.patch
Adds DuckDuckGo as default search engine, it's still changeable in settings.


#### disable-default-extensions.patch
Enabled user-modification for all extensions.
Disabled extensions:
* Hotword (incl. Shared Module)
* Google Now
* Google Feedback
* Cloud Print
* Google Webstore
* Network Speech synthesis
* Google Hangout


#### disable-autofill-download-manager.patch
Disables HTML-Form AutoFill data transmission. I don't know exactly when this is triggered, but it synchronizes the saved Form data with Google.


#### disable-google-url-tracker.patch
Disables URLTracker, which checks in which country you are to provide the closest google server for search lookups.
I know this class has a bad naming, but nevertheless it connects to Google.


#### disable-google-ipv6-probes.patch
Disables ipv6 probes to Google servers.
Google pings its own DNS server to check if ipv6 is available. Changed this to RIPE NCC k.root-servers.net. 2001:7fd::1 (anycasted).


#### disable-gcm-status-check.patch
Disables Google Cloud-Messaging status probes. GCM provides an interface to send messages directly to single devices, groups of devices, or devices subscribed to topics.


#### disable-missing-key-warning.patch
Disables warning dialog about missing Google API key.
This key is usually set on compile time and unique per distribution.
See [ArchLinux chromium PKGBUILD](https://projects.archlinux.org/svntogit/packages.git/tree/trunk/PKGBUILD?h=packages/chromium#n37) on how it's applied or this [HOWTO](https://www.chromium.org/developers/how-tos/api-keys) for an in-depth API key explanation.

Since we don't want to use these APIs at all, the keys are not set (at least for inox package on AUR).


#### disable-translation-lang-fetch.patch
Disables language fetching when settings are opened for the first time


#### disable-update-pings.patch
Disables update pings to https://clients2.google.com/service/update2 which is used for component updates.


#### chromium-sandbox-pie.patch
Hardening the sandbox with Position Independent Code(PIE) against ROP exploits.
This patch originally from openSUSE.


#### disable-new-avatar-menu.patch
Disables Google's new Avatar and signin menu.


#### disable-first-run-behaviour.patch
Modifies the first-run behaviour to prevent data leakage.


#### disable-battery-status-service.patch
The W3C Battery Status API[1] has quite a laughable statement:

"The information disclosed has minimal impact on privacy or
fingerprinting, and therefore is exposed without permission grants".

Along comes a paper "The leaking battery, A privacy analysis of the
HTML5 Battery Status API."

Clean up after the W3C and disable the battery status updater which
could be used to identity users[2].

[1] http://www.w3.org/TR/battery-status/
[2] https://eprint.iacr.org/2015/616.pdf

References: https://github.com/iridium-browser/iridium-browser/issues/40


#### modify-default-prefs.patch

DefaultCookiesSettings are temporary CONTENT_SETTING_DEFAULT.

Modifies following default settings (can be changed anytime):

User setting | new value
--- | ---
DefaultCookiesSetting      | ~~CONTENT_SETTING_SESSION_ONLY~~
EnableHyperLinkAuditing    | false
CloudPrintSubmitEnabled    | false
NetworkPredictionEnabled   | false
BackgroundModeEnabled      | false
BlockThirdPartyCookies     | true
AlternateErrorPagesEnabled | false
SearchSuggestEnabled       | false
AutofillEnabled            | false
"Send feedback" checkbox if user triggers settings-reset | false
BuiltInDnsClientEnabled    | false
SignInPromoUserSkipped     | true
SignInPromoShowOnFirstRunAllowed | false
ShowAppsShortcutInBookmarkBar | false
ShowBookmarkBar | true
PromptForDownload | true
SafeBrowsingEnabled | false
EnableTranslate | false
LocalDiscoveryNotificationsEnabled | false




#### branding.patch
s/Chromium/Inox/g


## Build flags
The packages hosted on AUR are configured to use following build config.
If you want to see how to apply a config flag view Chromium [Build Instructions](https://chromium.googlesource.com/chromium/src/+/master/docs/linux_build_instructions.md).

Feature | Build config
--- | ---
Disable google now |                enable_google_now=0
Disable WebRTC |                    enable_webrtc=0
Disable Remote service |          emable_remoting=0
Disable safe browsing |             safe_browsing_mode=0
Disable RLZ Identifier |              enable_rlz=0
Disable google hangouts |         enable_hangout_services_extension=0
Disable wifi bootstrapping |        enable_wifi_bootstrapping=0
Disable speech input |               enable_speech_input=0
Disable pre backups on sync |   enable_pre_sync_backup=0
Disable print preview |                enable_print_preview=0
Disable Chrome build |               google_chrome_build=0



## How to install extensions from Google WebStore?
Since there is no WebStore plugin, you cannot install extensions directly from the store, but you can download and install any extension manually.

    https://clients2.google.com/service/update2/crx?response=redirect&prodversion=48.0&x=id%3D[EXTENSION_ID]%26installsource%3Dondemand%26uc

To download a extension just replace [EXTENSION_ID] with the extension-id from the WebStore
(For example cjpalhdlnbpafiamejdnhcphjbkeiagm is the extension id of uBlock Origin).
You have 3 options to install an extension:


* **Drag and drop**

    Download the crx file with the browser, open `chrome://extensions` and drop the file from the download bar into the extensions tab.
    **Note:** Under some circumstances this method does not work on KDE Plasma.


* **Preference file**

    For example to install the extension aaaaaaaaaabbbbbbbbbbcccccccccc, create:
    `/usr/share/chromium/extensions/aaaaaaaaaabbbbbbbbbbcccccccccc.json`
    with following content:
    ```json
    {
        "external_crx": "/home/share/extension_1_0_0.crx",
        "external_version": "1.0.0"
    }
    ```
    If you restart Inox the extension should be loaded automatically.
    In near future /usr/share/chromium/ will be changed to /usr/share/inox/ to load independent extensions.

* **Extension loader**

    You can also use [extension-downloader](https://github.com/gcarq/inox-patchset/issues/7), it's a small python script to automate the download.

Keep in mind extensions are not updated automatically, so make sure you update them on a regular base.


## Contributing
Use the Issue Tracker for problems, suggestions, and questions, or visit the [Inox Browser thread](https://bbs.archlinux.org/viewtopic.php?id=198763) in the Arch forums.

You may also contribute by submitting pull requests.


## Credits
[Iridium Browser](https://iridiumbrowser.de/)



Bitcoin donations are welcome: 1EsahKzwNgZF56gmZZz8NVQJ4SWdGnshv4
