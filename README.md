# ACEMenu2

InDesign/Illustrator(AIRobin）/Photoshop/Acrobat/Bridgeが、カラー設定同期用ファイル「ACEConfigChache2.lst」に書き込んだカラー設定の内容をパースしてメニューバーに表示するアプリです。

Latest version　ダウンロードはこちらから（latestページで最新版をDLできます）：
[![Latest Release](https://img.shields.io/github/v/release/Yamonov/ACEMenu2?sort=semver)](https://github.com/Yamonov/ACEMenu2/releases/latest)

# UI

## メニューバー
<img width="696" height="982" alt="SS_Adobe Bridge 2025_20250727-214923@2x" src="https://github.com/user-attachments/assets/ef2ec15a-154a-4e1a-921a-001db4b5a43c" />

このアプリはあくまでも、カラー設定の同期用ファイルをパースして表示させるものです。
ACE未記載アプリは、カラー設定同期用ファイルにエントリを作っていないか、他のバージョンに上書きされている状態です。
アプリケーションのカラー設定が未設定になっているということではありません。

- InDesignにはバグがあり、メジャーバージョンごとのカラー設定エントリを作成できません。常に他のバージョンに上書きします。
さらに、ACEエントリにInDesignがあればそこから、エントリになければ他のアプリからカラー設定プリセット名を読み込み、勝手に設定してしまいます。
従ってInDesignは、バージョン毎に違うカラー設定にすることができません。
- Photoshop(beta)や(Prerelease)は、一般リリース版のうち最新のPhotoshopのカラー設定エントリを上書きします。
Photoshopはカラー設定に対して非常にアクティブで、アプリがアクティブになったときに即アクセスし、書き換えます。

このあたりの動作は、環境設定でACEConfigCache2.lstをリアルタイムで監視しながらアプリを切り替えてみるとよく分かります。

## 環境設定
<img width="3362" height="1562" alt="SS_ACEMenu2_20250727-215143@2x" src="https://github.com/user-attachments/assets/e5ff46dc-6af4-4930-afcc-59b039768f87" />

- 詳細バージョン表示
メニューリスト内に、メジャーバージョン（2025等）に加えて詳細バージョンを表示します。
- メニューバーにメジャーバージョン表示＆複数エントリがあるときのみ表示
メニューバー上にメジャーバージョンを表示します。InDesignやIllustratorはメニュー上にメジャーバージョンを表示しないため、複数バージョンを使い分けている方には便利でしょう。
ひとつのバージョンしかないときは表示させないようにもできます。
- 設定名をローカライズして表示
一般用 - 日本3など元々あるプリセットは、「Japan General Purpose 3」などをPhotoshop側でローカライズして表示しています。このアプリでもローカライズを行うために、
```~/Library/Application Support/ACEMenu2/ColorTranslation.plist```
でローカライズ処理をして表示させています。他の言語に対応させるときはこのplistを書き換えてください。
- 起動中のアプリにマークを付ける
メニュー内で起動中のアプリには、ACEエントリがある、ないに関わらずマークを付けます。
- メニューバーに同期アイコン表示
Acrobatを除いたACEエントリが全て同じなら、カラー設定が同期されていると見なしてマークを表示します。
- AIRobinを表示
Illustratorのバックグラウンド処理用のヘルパーアプリで、ACEエントリを持ちます。これと本体の設定は通常同じになりますが、食い違っているときに何かしらの不具合が出ているかもしれません。そのチェック用です。
- **アクティブなアプリを自動表示**
  Adobeアプリがアクティブになっていれば、メニューバー上の表示を切り替えます。ACEエントリがなくても表示します。
- Adobeアプリ以外が前面にあるとき、これを表示
ACEエントリのあるアプリを選択できます。Finderなどが前面にあるときは、このアプリを表示します。チェックオフでは、前の表示を継続します。
- **メニューバー表示アプリ切り替えモード**
オンにすると、メニュー項目を選択するとその項目がメニューバー上に表示されます。オフにすると、選択したアプリをアクティブにします。
- ログイン時に起動する
ログイン項目に自動登録します。
- 自動アップデート確認＆今すぐチェック
Sparkleライブラリを使用して、自動アップデートを試みます。
- ACEキャッシュファイルを削除
ACEConfigCache2.lstは同期用のキャッシュファイルです。削除しても、各アプリによって自動的に書き込まれていきます。
存在しない場合はPhotoshopをアクティブにすればすぐに作られます。また、カラー設定を開いてOKするだけでも作られます。
***このアプリは、ACEファイルを見るためのものです。ACEファイルがないとき、できるまで状態監視を続けます***
- ACEファイルの詳細を見る
ACEリストを開くを押すと、現在のACEエントリをリスト表示します。

## All Release Notes

See [Releases](https://github.com/Yamonov/ACEMenu2/releases) for the full version history and release notes.

# ACEMenu1について
[Qiita](https://qiita.com/yamo74/items/18f01dbb8db22ba3cfb5)
最初はテキストとしてコマンドを組み合わせてパースし、xBar（swiftBar）で表示。次にPythonでバイナリとして解析して表示。ACEMenu2はswiftアプリケーションとして作り直しました。

ACEConfigCache2.lstのバイナリ構造は以下です。これをパースしています。
<img width="1200" height="704" alt="https---qiita-image-store s3 ap-northeast-1 amazonaws com-0-35477-1835c6be-ccb4-4d25-afb3-b75235da3ca8" src="https://github.com/user-attachments/assets/fb853018-cd31-401e-b7de-9d5cdba28bd1" />
