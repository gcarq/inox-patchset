## What is this about?
Inox patchset is applied on the chromium source code and tries to prevent data transmission to Google Servers. So to say to remove Chromium from the cloud. The patches are split up based on features, so it's easy to patch only a subset of features.
The current patchset is applied on top of Chromium 45.0.2454.85.


## Warning
It is possible that some data is still transmitted(but down to a minimum) this is because Chromium is a quite large and complex codebase which changes each day.


# inox-patchset
If you are looking for a complete package there is a source(inox) and binary(inox-bin) version hosted for Arch linux in AUR[1,2].
These patches are tested and functional on Arch Linux x86_64.
Some Chromium features are also disabled via build flags during build (See below).

#### disable-instant-extended-api.patch
Disabled Google's Instant Extended API.
This has the effect that the old "New Tab" is in place without Google Search bar.

![alt text](http://i62.tinypic.com/29yi5t.jpg "inox-ntp-screen") 



#### add-duckduckgo-seaarch-engine.patch
Added DuckDuckGo as default search engine.


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
Disabled form AutoFill data transmission.


#### disable-google-url-tracker.patch
Disabled URLTracker, which checks in which country you are to provide the closest google server for search lookups. 
I know this class has a bad naming, but nevertheless it connects to Google.


#### modify-default-prefs.patch
Modified following default settings (can be changed anytime):

User setting | new value
--- | ---
DefaultCookiesSetting      | CONTENT_SETTING_SESSION_ONLY
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

#### restore-classic-ntp.patch
Restores old NTP (New Tab Page) and disables Google Login Menu.
The default NTP loads data from a web server to modify the appearance and inject a Google Search bar.


#### disable-google-ipv6-probes.patch
Disabled ipv6 probes to Google servers.
Google pings its own DNS server to check if ipv6 is available. Changed this to RIPE NCC k.root-servers.net. 2001:7fd::1 (anycasted).


####disable-gcm-status-check.patch
Disabled Google Cloud Messaging status probes.


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


## References

* [1] inox (Arch AUR): https://aur4.archlinux.org/packages/inox/
* [2] inox-bin (Arch AUR): https://aur4.archlinux.org/packages/inox-bin/
* [3] Chromium LinuxBuildInstructions: https://code.google.com/p/chromium/wiki/LinuxBuildInstructions#gyp_(configuring)

## Credits

Some patches are inspired from the Iridium Browser team. Thanks!

