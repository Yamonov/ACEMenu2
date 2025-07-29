# ACEMenu2

ACEMenu2 is a macOS menu bar app that parses and displays color settings synchronized by Adobe’s applications (InDesign, Illustrator, AIRobin, Photoshop, Acrobat, Bridge) stored in the “ACEConfigCache2.lst” file.

Download Latest Version
[![Latest Release](https://img.shields.io/github/v/release/Yamonov/ACEMenu2?sort=semver)](https://github.com/Yamonov/ACEMenu2/releases/latest)

# UI

## Menu Bar

<img width="696" height="982" alt="SS_Adobe Bridge 2025_20250727-214923@2x" src="https://github.com/user-attachments/assets/ef2ec15a-154a-4e1a-921a-001db4b5a43c" />

ACEMenu2 simply parses and displays color settings from the ACE synchronization file. Applications not listed in the ACE file either haven’t created an entry or their settings have been overwritten by another version. This does not mean that the application’s color settings are unset.
-	InDesign Bug: InDesign cannot create separate color setting entries per major version. It always overwrites the settings from other versions. Additionally, InDesign automatically applies color settings from its ACE entry if available; otherwise, it uses settings from other Adobe applications. Thus, different versions of InDesign cannot have different color settings.
-	Photoshop (Beta/Prerelease): These overwrite the latest stable Photoshop release’s color settings entry. Photoshop actively accesses and rewrites color settings whenever it becomes active.

You can better understand these behaviors by observing changes to ACEConfigCache2.lst in real-time while switching between applications using the preferences.

## Preferences

<img width="3362" height="1562" alt="SS_ACEMenu2_20250727-215143@2x" src="https://github.com/user-attachments/assets/e5ff46dc-6af4-4930-afcc-59b039768f87" />

- Show Detailed Version: Displays detailed version numbers in addition to major versions (e.g., 2025).
- Display Major Version on Menu Bar (Only if multiple entries exist): Shows major version numbers in the menu bar. Useful for distinguishing between multiple versions of applications like Illustrator or InDesign, which typically do not display major version numbers.
- Localize Color Setting Names: Color setting presets like “Japan General Purpose 3” are localized similarly to Photoshop. ACEMenu2 localizes these names using:

~/Library/Application Support/ACEMenu2/ColorTranslation.plist

Edit this plist to add support for other languages.

- Mark Active Applications: Indicates active Adobe apps in the menu, regardless of ACE entry existence.
- Show Sync Icon in Menu Bar: Displays a synchronization mark if ACE entries (excluding Acrobat) are identical.
- Show AIRobin: Displays the Illustrator background helper app (AIRobin), which also holds an ACE entry. Discrepancies between AIRobin and Illustrator may indicate issues.
- Automatically Display Active App: Updates menu bar display based on the active Adobe app, even if there is no ACE entry.
-	Display When Non-Adobe Apps Are Active: Choose an Adobe app to display when non-Adobe apps (e.g., Finder) are active. If unchecked, the previous selection persists.
-	Menu Bar Display Mode: If enabled, selecting a menu item changes the menu bar display to the selected app. If disabled, selecting an app activates it.
-	Launch at Login: Adds the app to login items.
-	Automatic Update Check & Check Now: Uses the Sparkle library to handle automatic updates.
-	Delete ACE Cache File: The ACEConfigCache2.lst file is a synchronization cache file. Deleting it triggers recreation by applications like Photoshop upon activation or when changing and saving color settings.
ACEMenu2 is designed to monitor the ACE file continuously and waits until the file is recreated if deleted.
-	View ACE File Details: Clicking “Open ACE List” displays the current ACE entries.

# All Release Notes

See [Releases](https://github.com/Yamonov/ACEMenu2/releases) for the full version history and release notes.

# About ACEMenu1

[Qiita](https://qiita.com/yamo74/items/18f01dbb8db22ba3cfb5)

Initially, the ACEConfigCache2.lst file was parsed and displayed as text using commands combined with xBar (swiftBar). The next version parsed it as binary using Python. ACEMenu2 has been rewritten as a Swift application.

The binary structure of ACEConfigCache2.lst, which ACEMenu2 parses, is shown below:

<img width="1200" height="704" alt="https---qiita-image-store s3 ap-northeast-1 amazonaws com-0-35477-1835c6be-ccb4-4d25-afb3-b75235da3ca8" src="https://github.com/user-attachments/assets/fb853018-cd31-401e-b7de-9d5cdba28bd1" />
