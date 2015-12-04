## What is this about?
Inox patchset is applied on the chromium source code and tries to prevent data transmission to Google to get a minimal chromium based browser. The patches are split up based on features, so it's easy to patch only a subset of them.
The current patchset is applied on top of Chromium 47.0.2526.73.


## Warning
It is possible that some data is still transmitted(but down to a minimum) this is because Chromium is a quite large and complex codebase which changes each day.


# inox-patchset 47.0.2526.73
If you are looking for a complete package there is a source(inox) and binary(inox-bin) version hosted for Arch linux in AUR[1,2].
These patches are tested and functional on Arch Linux x86_64.
Some Chromium features are also disabled via build flags during build (See below).


#### restore-classic-ntp.patch
Restores old NTP (New Tab Page).
The default NTP loads data from a web server to modify the appearance and inject a Google Search bar with a unique identifier.

![alt text](http://i62.tinypic.com/29yi5t.jpg "inox-ntp-screen") 


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
* Bookmark Manager


#### disable-autofill-download-manager.patch
Disables HTML-Form AutoFill data transmission. 


#### disable-google-url-tracker.patch
Disables URLTracker, which checks in which country you are to provide the closest google server for search lookups. 
I know this class has a bad naming, but nevertheless it connects to Google.


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


#### disable-google-ipv6-probes.patch
Disables ipv6 probes to Google servers.
Google pings its own DNS server to check if ipv6 is available. Changed this to RIPE NCC k.root-servers.net. 2001:7fd::1 (anycasted).


####disable-gcm-status-check.patch
Disables Google Cloud-Messaging status probes. GCM provides an interface to send messages directly to single devices, groups of devices, or devices subscribed to topics.


####disable-missing-key-warning.patch
Disables warning dialog about missing Google API key.
This key is usually set on compile time and unique per distribution. 
See [ArchLinux chromium PKGBUILD](https://projects.archlinux.org/svntogit/packages.git/tree/trunk/PKGBUILD?h=packages/chromium#n37) on how it's applied or this [HOWTO](https://www.chromium.org/developers/how-tos/api-keys) for an in-depth API key explanation.

Since we don't want to use these APIs at all, the keys are not set (at least for inox package on AUR).


####disable-translation-lang-fetch.patch
Disables language fetching when settings are opened for the first time


####disable-update-pings.patch
Disables update pings to https://clients2.google.com/service/update2 which is used for component updates.


####chromium-sandbox-pie.patch
Hardening the sandbox with Position Independent Code(PIE) against ROP exploits.
This patch originally from openSUSE.



####disable-new-avatar-menu.patch
Disables Google's new Avatar Menu.


####disable-first-run-behaviour.patch
Modifies the first-run behaviour to prevent data leakage.


####branding.patch
s/Chromium/Inox/g


## Build flags
The packages hosted on AUR[1,2] are configured to use following build config.
If you want to see how to apply a config search for Chromium LinuxBuildInstructions[3].

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

    https://clients2.google.com/service/update2/crx?response=redirect&prodversion=45.0&x=id%3D[EXTENSION_ID]%26installsource%3Dondemand%26uc

To download a extension just replace [EXTENSION_ID] with the extension-id from the WebStore.
(For example gighmmpiobklfepjocnamgkkbiglidom is the extension id from AdBlock)

To install it, just drag and drop the downloaded file into a chrome://extensions/ tab.

Keep in mind extensions are not updated automatically, so make sure you update them on a regular base.


## References

* [1] inox (Arch AUR): https://aur.archlinux.org/packages/inox/
* [2] inox-bin (Arch AUR): https://aur.archlinux.org/packages/inox-bin/
* [3] Chromium LinuxBuildInstructions: https://chromium.googlesource.com/chromium/src/+/master/docs/linux_build_instructions.md

## Credits

Some patches are inspired from the Iridium Browser team. Thanks!



Bitcoin donations are welcome: 1EsahKzwNgZF56gmZZz8NVQJ4SWdGnshv4
