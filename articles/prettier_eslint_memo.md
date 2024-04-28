---
title: "PrettierとESLintの導入備忘録"
emoji: "📌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Prettier","ESLint"]
published: false
---

## Prettier
### Prettierをインストール
  ```
  npm install -D prettier
  ```
  ※ nodeが入っていない場合は入れる必要あり。

### Prettierの実行
  - 変更点確認
    ```
    npx prettier --check (対象)
    ```
  - 書き換え
    ```
    npx prettier --write (対象)
    ```

### package.jsonに以下を追記
  ```
  "scripts": {
    "format": "prettier --write ."
  },
  ```
  これで、`npm run format`で全ファイルに対して書き換えが実行できる

### シングルクオートの設定を追加
  - .prettierrcファイルを作成する。（Prettierの設定ファイル）
  - .prettierrcファイルに以下のような設定を記載する。
    ```
    {
      "singleQuote": true
    }
    ```


## ESLint

### ESLintのインストール
  ```
  npm install eslint eslint-config-prettier eslint-config-standard
  ```
  ※ ESLintとPrettierの競合するルールを無効化するために、[eslint-config-prettier](https://github.com/prettier/eslint-config-prettier)もインストール。
  ※ 今回[JavaScript Standard Style](https://standardjs.com/)に準拠してリントチェックを行うため、[eslint-config-standard](https://github.com/standard/eslint-config-standard) もインストール


### ESLintの初期化
  プロジェクトのルートディレクトリで以下のコマンドを実行して、ESLintの初期設定を行います。
  ```
  npx eslint --init
  ```

  このコマンドを実行すると、対話型のセットアップが始まり、以下のような質問がされる。
  - ESLintの使用方法を選択
    ```
    How would you like to use ESLint? … 
    To check syntax only
    To check syntax and find problems
    To check syntax, find problems, and enforce code style //自分はこれを選択
    ```
  - プロジェクトで使用するモジュールの種類
    ```
    What type of modules does your project use? … 
    JavaScript modules (import/export) //自分はこれを選択
    CommonJS (require/exports)
    None of these
    ```
    Node.jsの場合CommonJS、それ以外はJavaScript modulesで良さそう（[参考](https://zenn.dev/yodaka/articles/596f441acf1cf3)）
  - TypeScriptを使うかどうか
    ```
    ? Does your project use TypeScript? … 
      No
      Yes //自分はこれを選択
    ```
  - コードの実行環境
    ```
    ? Where does your code run? …  (Press <space> to select, <a> to toggle all, <i> to invert selection)
    ✔ Browser //自分はこれを選択
    ✔ Node
    ```
  - 準拠するスタイルガイド
    ```
    ? Which style guide do you want to follow? … 
    ❯ Standard: https://github.com/standard/eslint-config-standard-with-typescript  //自分はこれを選択
      XO: https://github.com/xojs/eslint-config-xo-typescript?
    ```
  - 以下の依存関係をインストールするか
    ```
    The config that you've selected requires the following dependencies:
    eslint, globals, eslint-config-standard-with-typescript, @typescript-eslint/eslint-plugin@^6.4.0, eslint@^8.0.1, eslint-plugin-import@^2.25.2, eslint-plugin-n@^15.0.0 || ^16.0.0 , eslint-plugin-promise@^6.0.0, typescript@*, eslint-plugin-react, @eslint/eslintrc, @eslint/js
    ? Would you like to install them now? › No / Yes //Yesを選択
    ```
  - どのパッケージマネージャを使うか
    ```
    ? Which package manager do you want to use? … 
    ❯ npm //自分はこれを選択
      yarn
      pnpm
      bun
    ```

### ESLintの実行
  ESLintを実行コマンドは以下。
  ```
  npx eslint (オプション) (対象ファイル)
  ```
  オプションには以下のようなものがある
  - `--fix`: 自動修正を試みます。
  - `--ext <extension>`: 特定のファイル拡張子のみを対象にします。
  - `--config <path>`: 指定した設定ファイルを使用します。
  - `--ignore-path <path>`: 指定したパスのファイルを無視します。
  - `--quiet`: 警告やエラー以外の出力を抑制します。
  - `--env <environment>`: 特定の環境におけるグローバル変数を定義します。


### package.jsonに以下を追記
  ```
  "scripts": {
      "lint": "eslint --fix ."
    },
  ```
  これでnpm run lintコマンドでESLintを実行できる。


参考URL
- [Prettierの導入方法 フロントエンド開発で必須のコード整形ツール](https://ics.media/entry/17030/)
- [フロントエンドやるなら入れておくべきPrettierってなに？](https://qiita.com/mzmz__02/items/12d198b696efa8b29bda)
- [フロントエンドやるなら入れておくべきESlintってなに？](https://qiita.com/mzmz__02/items/63f2624e00c02be2f942)
- [Prettier 入門 ～ESLintとの違いを理解して併用する～](https://qiita.com/soarflat/items/06377f3b96964964a65d)