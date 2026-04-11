# ACEMenu Plus（ACEMenu3）

InDesign/Illustrator(AIRobin）/Photoshop/Acrobat/Bridgeが、カラー設定同期用ファイル「ACEConfigChache2.lst」に書き込んだカラー設定の内容をパースしてメニューバーに表示するアプリです。optionキーを押しながらメニュー選択すると、起動中のアプリならそのカラー設定を直接開きます。

Plusバージョンから、SCRIPTMETAに対応しました。
[SCRIPTMETA仕様](https://gist.github.com/Yamonov/31698801e781a6c6fa606634d34f771e)

Latest version　ダウンロードはこちらから（latestページで最新版をDLできます）：
[Latest](https://github.com/Yamonov/ACEMenu2/releases/tag/v3.0.3)

# UI

## メニューバー
<img width="362" height="517" alt="SS_Safari_07_003339" src="https://github.com/user-attachments/assets/1f5e0d2f-5fbc-412e-beb5-ad560c7012c7" />

最前面のアプリアイコン、メジャーバージョン、カラー設定プリセット名称をメニューバーに表示します。

登録したスクリプトにアップデートがあるときは、上矢印アイコンをそのあとに表示します。

**このアプリはあくまでも、カラー設定の同期用ファイルをパースして表示させるものです。**

ACE未記載と表示されているアプリは、カラー設定同期用ファイルにエントリを作っていないか、他のバージョンに上書きされている状態です。

アプリケーションのカラー設定が未設定になっているということではありません。

- InDesignにはバグがあり、メジャーバージョンごとのカラー設定エントリを作成できません。常に他のバージョンに上書きします。

  - さらに、ACEエントリにInDesignがあればそこから、エントリになければ他のアプリからカラー設定プリセット名を読み込み、勝手に設定してしまいます。
従ってInDesignは、バージョン毎に違うカラー設定にすることができません。

- Photoshop(beta)や(Prerelease)は、一般リリース版のうち最新のPhotoshopのカラー設定エントリを上書きします。

  - Photoshopはカラー設定に対して非常にアクティブで、アプリがアクティブになったときに即アクセスし、書き換えます。

このあたりの動作は、環境設定でACEConfigCache2.lstをリアルタイムで監視しながらアプリを切り替えてみるとよく分かります。

## 環境設定
<img width="474" height="858" alt="SS_ACEMenu Plus_07_003341" src="https://github.com/user-attachments/assets/b4df8182-db78-4aa5-9a68-df09608a35ec" />
<img width="1025" height="856" alt="SS_ACEMenu Plus_07_003343" src="https://github.com/user-attachments/assets/242f6c58-eb13-44de-9615-3eaf8dfe7248" />


- ■詳細バージョン表示
  - メニューリスト内に、メジャーバージョン（2025等）に加えて詳細バージョンを表示します。
- ■メニューバーにメジャーバージョン表示＆複数エントリがあるときのみ表示
  - メニューバー上にメジャーバージョンを表示します。InDesignやIllustratorはメニュー上にメジャーバージョンを表示しないため、複数バージョンを使い分けている方には便利でしょう。
ひとつのバージョンしかないときは表示させないようにもできます。
- ■設定名をローカライズして表示
  - 一般用 - 日本3など元々あるプリセットは、「Japan General Purpose 3」などをPhotoshop側でローカライズして表示しています。このアプリでもローカライズを行うために、
```~/Library/Application Support/ACEMenu2/ColorTranslation.plist```
でローカライズ処理をして表示させています。他の言語に対応させるときはこのplistを書き換えてください。
- ■起動中のアプリにマークを付ける
  - メニュー内で起動中のアプリには、ACEエントリがある、ないに関わらずマークを付けます。
- ■メニューバーに同期アイコン表示
  - Acrobatを除いたACEエントリが全て同じなら、カラー設定が同期されていると見なしてマークを表示します。
- ■AIRobinを表示
  - Illustratorのバックグラウンド処理用のヘルパーアプリで、ACEエントリを持ちます。これと本体の設定は通常同じになりますが、食い違っているときに何かしらの不具合が出ているかもしれません。そのチェック用です。
- **■アクティブなアプリを自動表示**
  -   Adobeアプリがアクティブになっていれば、メニューバー上の表示を切り替えます。ACEエントリがなくても表示します。
- ■Adobeアプリ以外が前面にあるとき、これを表示
  - ACEエントリのあるアプリを選択できます。Finderなどが前面にあるときは、このアプリを表示します。チェックオフでは、前の表示を継続します。
- ■メニューバー表示アプリ切り替えモード
  - 3.0.3でこの機能は削除しました。
- ■ログイン時に起動する
  - ログイン項目に自動登録します。
- ■自動アップデート確認＆今すぐチェック
  - Sparkleライブラリを使用して、自動アップデートを試みます。
- ■ACEキャッシュファイルを削除
  - ACEConfigCache2.lstは同期用のキャッシュファイルです。削除しても、各アプリによって自動的に書き込まれていきます。
存在しない場合はPhotoshopをアクティブにすればすぐに作られます。また、カラー設定を開いてOKするだけでも作られます。
***このアプリは、ACEファイルを見るためのものです。ACEファイルがないとき、できるまで状態監視を続けます***
- ■ヘルプ表示
  - 一度は目を通してください。   
- ■ACEファイルの詳細を見る
  - ACEリストを開くを押すと、現在のACEエントリをリスト表示します。
 
### SCRIPT管理
<img width="1015" height="846" alt="SS_ACEMenu Plus_07_003345" src="https://github.com/user-attachments/assets/9172b876-23f9-4eb3-ba18-8b59f0b0bb12" />

Plusバージョン（Version3.0.3）からは、jsxなどのテキストスクリプトのアップデートをチェックできるようにする仕組み **SCRIPTMETA** に対応させました。スクリプトの入っている複数のフォルダを登録でき、内容にSCRIPTMETAタグのあるスクリプトをリストアップ、更新チェックを行います。フォルダを登録していなければ、この機能はオフになります。

Photoshop、Illustrator、InDesignのscriptsフォルダを登録、SCRIPTMETA対応のjsx等の更新をチェックできるようになります。



## All Release Notes

See [Releases](https://github.com/Yamonov/ACEMenu2/releases) for the full version history and release notes.

# ACEMenu1について
[Qiita](https://qiita.com/yamo74/items/18f01dbb8db22ba3cfb5)
最初はテキストとしてコマンドを組み合わせてパースし、xBar（swiftBar）で表示。次にPythonでバイナリとして解析して表示。ACEMenu2はswiftアプリケーションとして作り直しました。

ACEConfigCache2.lstのバイナリ構造は以下です。これをパースしています。
<img width="1200" height="704" alt="https---qiita-image-store s3 ap-northeast-1 amazonaws com-0-35477-1835c6be-ccb4-4d25-afb3-b75235da3ca8" src="https://github.com/user-attachments/assets/fb853018-cd31-401e-b7de-9d5cdba28bd1" />
