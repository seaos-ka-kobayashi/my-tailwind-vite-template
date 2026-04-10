# TailWindCSSーVite環境構築用テンプレート

## 1.利用プロジェクトへファイル一式ダウンロード
プロジェクト名フォルダ作成時に以下のコマンドを実行することで<br>
TailWindCSS-Vite環境構築に必要なファイル一式をダウンロードします。

```npx degit git@github.com:seaos-ka-kobayashi/my-tailwind-vite-template my-new-project```

## 2.プロジェクトディレクトリでパッケージをインストール
該当のプロジェクトディレクトリに移動し以下のコマンドを実行して関連パッケージをインストールします。

```npm install```

## 3.開発環境起動
以下のコマンドで開発環境を立ち上げます。

```npm run dev```

## 4.HPなどへの設置用のファイル書き出し
以下のコマンドをルートディレクトで実行しデプロイします。
dist/フォルダが生成され、単独LP用のHTML構成ファイルが書き出しされます。

```npm run build```
