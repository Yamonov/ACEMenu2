# ACEMenu2

The menu bar displays the color settings preset names for Adobe applications.
It shows the contents written in the color settings sync file, “ACEConfigCache2.lst”, so the displayed information may not match the current state of the apps.
To update the display to match the current settings, open the color settings dialog in each app and click OK. This will write the current settings to the sync file.

Even if an Adobe app (Photoshop, InDesign, Illustrator, Bridge, or Acrobat) does not have an entry in the sync file, it will still appear in the menu when running. Selecting an app from the menu will bring it to the front.

You can also display the major version in the menu bar, so you can see the version of the active app at a glance. Unlike Photoshop, InDesign and Illustrator do not show the version number in their own menus, so this feature is useful for users who work with multiple versions.

InDesign/Illustrator(AIRobin）/Photoshop/Acrobat/Bridgeが、カラー設定同期用ファイル「ACEConfigChache2.lst」に書き込んだカラー設定の内容をパースしてメニューバーに表示するアプリです。

Bridgeの編集＞カラー設定で設定同期を行うと、まずBridgeがこのファイルに設定（プリセット）名を書き込みます。
他のアプリケーションは、起動時またはアクティブになったときに一度だけ、Bridgeが書き込んだ設定にカラー設定を変更します。
また、Bridge以外でカラー設定を変更すると、このファイルに設定内容を書き込みます。これは通常バージョンごとに書き込まれます。

ただし、Photoshop(beta）やInDesignは、バージョンを無視して一つのエントリに設定を上書きする、というバグがあります（仕様ではなく、バグです）。
このため
- Photoshop最新版＋PhotoshopBetaを同時起動していると、どちらかがアクティブになったときに自身の設定を上書きする。
  - ACEMenu2上では、アクティブでないPhotoshopはACECacheファイルにエントリがないため（ACE記載なし）となる
- 複数バージョンのInDesignを起動しているとき、アクティブになったInDesignに、非アクティブなInDesignのカラー設定が共有される

ということが起きます。

設定内にエントリがなくてもメニュー内には表示しますが、あくまでもカラー設定同期用ファイルを見るだけなので、このような動作になることを忘れないようにしてください。
Photoshopは常にアクティブになった瞬間に自身の設定を書き込むため、メニューバー上では正しく現在のカラー設定内容が表示されます。

Latest version　ダウンロードはこちらから。：
[![Latest Release](https://img.shields.io/github/v/release/Yamonov/ACEMenu2?sort=semver)](https://github.com/Yamonov/ACEMenu2/releases/latest)

## All Release Notes

See [Releases](https://github.com/Yamonov/ACEMenu2/releases) for the full version history and release notes.

# バイナリ構造
<img width="1200" height="704" alt="https---qiita-image-store s3 ap-northeast-1 amazonaws com-0-35477-1835c6be-ccb4-4d25-afb3-b75235da3ca8" src="https://github.com/user-attachments/assets/fb853018-cd31-401e-b7de-9d5cdba28bd1" />

# ACEMenu1
[Qiita](https://qiita.com/yamo74/items/18f01dbb8db22ba3cfb5)
最初はテキストとしてコマンドを組み合わせてパースし、xBar（swiftBar）で表示。次にPythonでバイナリとして解析して表示。ACEMenu2はswiftアプリケーションとして作り直しました。

# メニュー内容
<img width="546" height="863" alt="SS_CleanShot_20250714-195622" src="https://github.com/user-attachments/assets/ff0f6805-793e-44ec-927e-6c4168ab1ba4" />

# 環境設定
<img width="512" height="847" alt="SS_ 2025-07-14 19 59 10" src="https://github.com/user-attachments/assets/b991f7f6-983b-419f-a6b5-66b1021dc702" />
