# SEAOSモックアップ用テンプレート（TailwindCSS v4 + Vite + Sass）

SEAOSサービスページの実装前モックアップを作成するためのテンプレートです。
[seaos-design-system](https://github.com/seaosinc/seaos-design-system) のデザイントークンを同梱しており、
`bg-active-dark` や `text-base` などトークン由来のユーティリティクラスをそのまま使ってモックアップを作成できます。

## 使い方

### 1. 利用プロジェクトへファイル一式ダウンロード

プロジェクト名フォルダ作成時に以下のコマンドを実行することで、環境構築に必要なファイル一式をダウンロードします。

```npx degit seaos-ka-kobayashi/my-tailwind-vite-template my-new-project```

### 2. プロジェクトディレクトリでパッケージをインストール

該当のプロジェクトディレクトリに移動し、以下のコマンドを実行して関連パッケージをインストールします。

```npm install```

### 3. 開発環境起動

以下のコマンドで開発環境を立ち上げます。

```npm run dev```

### 4. HPなどへの設置用のファイル書き出し

以下のコマンドをルートディレクトリで実行します。
dist/フォルダが生成され、単独LP用のHTML構成ファイルが書き出しされます。

```npm run build```

## ファイル構成

```
├── index.html          # モックアップの起点（複数ページはHTMLを追加）
├── vite.config.js      # Vite + @tailwindcss/vite プラグイン
└── src/
    ├── main.js         # theme.css と custom.scss を読み込み
    ├── tokens.css      # SEAOSデザイントークン（正典の写し・編集しない）
    ├── theme.css       # トークン → Tailwindユーティリティ生成（@theme inline）
    └── custom.scss     # モックアップ固有の自由記述スタイル（Sass）
```

## デザイントークン

- `src/tokens.css` は [seaos-design-system](https://github.com/seaosinc/seaos-design-system) の
  `docs/.vitepress/theme/tokens.css`（正典＝デザイントークンガイドの写し）のコピーです。
  ガイドが更新されたら本ファイルも追随させてください。値をこのファイルで独自に変更しないでください。
- `src/theme.css` がトークンをTailwindユーティリティに変換します
  （`seaos-ui-component-vue` の `theme.css` と同じ `@theme inline` パターン）。
  色（`bg-active-dark` 等）・フォントサイズ（`text-base` = 0.875rem 等）・
  spacing（8px基準、`p-1` = 8px）がトークン由来になります。

## Sassとの併用ルール

Tailwind v4はSassとの直接連携をサポートしないため、2系統に分離しています。

- `theme.css` / `tokens.css` は **`.css` のまま**にする（Sassに通さない）
- `.scss` 内では `@apply` などTailwindの機能を**使わない**
- `.scss` からトークンを参照するときは `var(--color-active-dark)` のように**CSS変数で参照**する
- ネスト・`@use`・`@mixin` などSassの機能は `custom.scss` 側で自由に使えます

## 旧バージョン（Tailwind v3 + SCSS構成）

v4化以前の構成が必要な場合は `v3` タグから取得できます。

```npx degit seaos-ka-kobayashi/my-tailwind-vite-template#v3 my-new-project```
