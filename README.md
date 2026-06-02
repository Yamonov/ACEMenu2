# ACEMenu Plus（ACEMenu3）

[あたらしい説明ページはこちら](https://iwashi.org/app/acemenu-plus/ja/index.html)

InDesign/Illustrator(AIRobin）/Photoshop/Acrobat/Bridgeが、カラー設定同期用ファイル「ACEConfigChache2.lst」に書き込んだカラー設定の内容をパースしてメニューバーに表示するアプリです。optionキーを押しながらメニュー選択すると、起動中のアプリならそのカラー設定を直接開きます。

Plusバージョンから、SCRIPTMETAに対応しました。
[SCRIPTMETA仕様](https://github.com/Yamonov/SCRIPTMETA))

Latest version　ダウンロードはこちらから（latestページで最新版をDLできます）：
[Latest](https://github.com/Yamonov/ACEMenu2/releases/tag/v3.0.3)

Illustrator、InDesign、Photoshop統合タブ型スクリプトランチャーの[Scripta!](https://github.com/Yamonov/Scripta) もどうぞ。

## All Release Notes

See [Releases](https://github.com/Yamonov/ACEMenu2/releases) for the full version history and release notes.

# ACEMenu1について
[Qiita](https://qiita.com/yamo74/items/18f01dbb8db22ba3cfb5)
最初はテキストとしてコマンドを組み合わせてパースし、xBar（swiftBar）で表示。次にPythonでバイナリとして解析して表示。ACEMenu2はswiftアプリケーションとして作り直しました。

ACEConfigCache2.lstのバイナリ構造は以下です。これをパースしています。
<img width="1200" height="704" alt="https---qiita-image-store s3 ap-northeast-1 amazonaws com-0-35477-1835c6be-ccb4-4d25-afb3-b75235da3ca8" src="https://github.com/user-attachments/assets/fb853018-cd31-401e-b7de-9d5cdba28bd1" />
