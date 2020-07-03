# gulp + EJS ボイラーテンプレート

gulp + EJSでのWebサイト構築用ボイラーテンプレートです。
HTMLファイルの自動構築、Sassの自動コンパイル、ESの自動トランスパイルとそのプレビューをローカルサーバーにて行います。
gulpがNode.jsにて動作しターミナルで操作するという特性上、Visual Studio Codeとの相性がかなり高いです。

[Visual Studio Code]
https://code.visualstudio.com/



# 開始方法

1. Node.jsのインストール

2. npmを最新にする
   npm install -g npm

3. gitクライアントのインストール

～～～ ここで一旦再起動 ～～～

4. gulpのグローバルインストール
   npm i -g gulp-cli

～～～ 既に環境がある場合はここから ～～～

5. Visual Studio Codeにてディレクトリを開く

6. gulpのローカルインストール
   npm i -D gulp

7. パッケージインストール
   npm i

8. developmentを実行

9. serveを実行
   http://localhost:3000 でプレビュー閲覧

以降、serveの実行のみで自動処理が走ります。
serve実行中はファイルの変更を監視し、ファイルの変更とともにコンパイラが動作しブラウザ更新まで自動化されます。



# 構築系コマンド

サイト構築時に使用します。serve以外はdevelopmentの機能別コマンドとなっています。

``` bash
# serve mode：各種コンパイルタスクを利用出来ます。通常はこちらで制作を行います。
npm run serve

# development mode：developmentビルドを行います。`dist/`配下に書き出されます。
npm run development

# img recompile task：画像再圧縮タスクです。`src`と`dist`で画像数が合わなくなった場合にリセット目的で使用します。
npm run img

# ejs recompile task：ejsファイルの再コンパイルタスクです。`dist`に書き出されたHTMLファイルを全削除し、再度出力します。
npm run ejs

# json file check task：各種jsonファイルのチェックタスクです。
npm run json-check

```



# デプロイ系コマンド

本番公開を行う際は以下タスクを実行する事で書き出しが可能です。

``` bash
# production：ルートパスでproductionビルドを行います。`dist-production/`配下に書き出されます。
npm run production

# production-fullpath：PATH名が`setting.json`ファイルの`siteDomain`を用いproductionビルドを行います。`dist-production-fullpath/`配下に書き出されます。
npm run production-fullpath

# zip：ルートパスでproductionビルドを行い、.zipファイルとして`setting.json`ファイルで`publishDir`にて指定したディレクトリへ書き出します。
npm run zip

```



# lint系コマンド

コードの正当性を検査します。
HTMLのlintについては「https://validator.w3.org/」を利用してください。

``` bash
# lint css：CSS / SCSSファイルのlintタスクです
npm run lint:css

# lint fix css：CSS / SCSSファイルの自動修正タスクです
npm run fix:css

# lint js：JSファイルのlintタスクです
npm run lint:js

# lint fix js：JSファイルの自動修正タスクです
npm run fix:js

```



# ディレクトリ構造

第2階層までのディレクトリ構造です。`src`ディレクトリが作業ディレクトリになり、`dist`ディレクトリを出力先として利用します。納品タスクでコピーされるディレクトリも`dist`になります。

``` bash
|-- dist #納品ディレクトリ
|   |-- assets
|   |   |-- css/
|   |   |-- fonts/
|   |   |-- images/
|   |   |-- js/
|   |-- page2
|   |-- page3
|   |-- sitemap
|   |-- index.html
|-- src
|   |-- assets
|   |   |-- css/
|   |   |-- images/
|   |   |-- js/
|   |-- inc
|   |-- page2
|   |-- page3
|   |-- sitemap
|   |-- index.ejs
|-- .babelrc
|-- .editorconfig
|-- .eslintrc.json
|-- .stylelintrc.json
|-- define.json
|-- setting.json
|-- setting.json.sample
|-- gulpfile.js
|-- package-lock.json
|-- package.json
|-- README.md
|-- setting-site.json
|-- webpack.config.js
|-- webpack.production.config.js
```



# 仕様

仕様及び対応環境は以下の通りです。

| 項目 | 詳細 |
| --- | --- |
| パッケージマネージャー | npm |
| コンパイル環境、タスクランナー | Gulp v4 |
| テンプレートエンジン | EJS |
| CSS トランスパイラ | SCSS + Gulp |
| CSS設計 | FLOCSS |
| JavaScript モジュールバンドラ | Webpack |
| JavaScript ライブラリ | Vanilla JS（Pure JS） |
| JavaScript モジュールバンドラ | Webpack |
| インストールパッケージリスト | 参照：`package.json` |
| Lint環境 | ESlint / Stylelint |



# フロント側プラグイン

以下プラグインはデフォルトでインストールされています。

| プラグイン名 | 用途 |
| --- | --- |
| ress | ress.css |
| object-fit-images | `object-fit`のPolyfill |
| picturefill | `<picture>`タグのPolyfill |
| sweet-scroll | ページスクロール用プラグイン |
| swiper | スライダー用プラグイン |
| yakuhanjp | 約物半角化用日本語フォント |



# 対応ブラウザ

全て最新バージョンに対応。

| ブラウザ名 | 対応バージョン |
| --- | --- |
| Google Chrome | 最新 |
| Firefox | 最新 |
| Safari(macOS) | 最新 |
| IE11 | Windows10 |
| Edge | 最新 |
| Safari(iOS) | 最新iOS |
| Google Chrome(Android) | 最新 |



# コーディング規約について

- 全体：`.editorconfig`をご参照ください。
- JavaScript：`.eslintrc.json`をご参照ください。
- Sass：`.stylelintrc.json`をご参照ください。



# その他設定について

- 環境設定ファイルに`setting.json`が存在します。各環境に合わせてご指定ください。
- サイト設定ファイルに`setting-site.json`が存在します。値を指定することで.ejsファイルにて読み込むことが可能です。
- EJSで用いる定数は`define.json`に記述されています。



# FLOCSSについて

Foundation Layout Object CSS
Sassのファイル構成や命名規則を取り決めた設計思想です。
https://github.com/hiloki/flocss


``` bash
#ファイル構成（*：サイトによって内容が増減する）
|-- fundation #デフォルトスタイルとを管理
|   |-- reset #スタイルリセット（当ボイラーではress.cssを利用）
|   |-- base #根幹のスタイルで、基本的にはタグセレクタを使用
|   |-- variable #文字色やコンテンツ幅などを変数で管理
|   |-- mixin #mixin、functionを管理
|-- layout #サイト全体の共通エリアを管理 *
|   |-- base #基本レイアウト
|   |-- header #ヘッダー
|   |-- main #メインコンテンツ
|   |-- sidebar #サイドバー
|   |-- footer #フッター
|   |-- breadcrumbs #パンくずリスト
|-- object #ビジュアルパターンを管理
|   |-- component #パーツモジュールを管理 *
|   |   |-- title #見出し
|   |   |-- button #ボタン（アンカー含む）
|   |   |-- form #フォームとそのパーツ
|   |   |-- table #テーブル
|   |   |-- hamburger #ハンバーガー
|   |-- project #共通化されない要素を管理（主に各ページのレイアウト） *
|   |   |-- 404 #404ページ
|   |   |-- top #(ページ名)
|   |-- utility #その他補助的な役割 *
|   |   |-- plugin #プラグインの基本設定


#ファイル名（命名規則）
フォルダ名の頭文字をプレフィックスとして付与します。
ex) _f-base.scss、_l-header.scss


#MindBEMding
Block__Element--Modifier
ex) .l-header__nav--sp、.p-404__text

scss上では&で内部継承して一纏めにします。
ボタンの色違いなどは基本レイアウトを@extendで外部継承します。


#Google HTML/CSS Style Guide（一部抜粋）
1. プロパティはアルファベット順に記述
2. ショートハンドを使用
3. 引用符にはシングルクォーテーションを使う
```
