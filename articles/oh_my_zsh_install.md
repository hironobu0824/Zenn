---
title: "いい加減Oh My Zsh!を入れた"
emoji: "📚"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: true
---
## Oh My Zsh!とは
Zshシェルのためのカスタマイズと管理を容易にするフレームワーク。
プロンプトのテーマやプラグイン、便利なショートカットなどを簡単に設定できる。
- [公式サイト](https://ohmyz.sh/)

## 経緯
２年以上ターミナルをほぼデフォルトの状態で使っていたが、突然コマンドを直打ちするのが面倒になり、自動補完できるようにしたいと思った。
なんとなく存在を知っていたOh My Zsh！を調べ、拡張機能を入れることで自動補完できると知り、導入に至った。


## 環境
- mac（ターミナル）（Zsh）

## やったこと
##### 1. [公式サイト](https://ohmyz.sh/#install)からコマンドを確認し、インストール
   ```
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```
   インストール完了後、以下のように見た目が変化。
   (before) 
   <img src='/images/image1.png' width='70%'>
   (after)
   <img src='/images/image2.png' width='50%'><br>
  
  <詳細>
    Oh My Zsh!がインストールされるとzshシェルの設定ファイルである`~/.zshrc`が上書かれ、`~/.oh-my-zsh`というディレクトリが置かれる。
<br>

##### 2. テーマを変更
テーマは`~/.zshrc` 内で以下のように設定されていて、デフォルトでは`robbyrussell`という値が入っている。
この値に、以下の公式URLから選んだテーマを設定すると変更できる。
https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
私は、'simple'というテーマに変更。

```
source ~/.zshrc
```
で反映すると、以下のようなデザインに変わった。(ターミナル再起動でも可)

<img src='/images/image3.png' width='60%'>

##### 3. プラグインのインストール
プラグインは[公式サイト](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins-Overview)に記載されているものと、[zsh-usersというGithubプロジェクト](https://github.com/zsh-users)に記載されているユーザーが作ったものと２種類ある。

⚪︎ 公式サイトの方法
- [公式サイト](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins-Overview)でプラグイン一覧を確認する。
- `~/.zshrc` 内の`plugins` の値に以下の様に記載。
  ```
  plugins=(git docker)
  ```
- `source ~/.zshrc` かターミナル再起動で反映


⚪︎ zsh-usersの方法
- [zsh-users](https://github.com/zsh-users)にあるリポジトリを、`~/.oh-my-zsh/custom/plugins/` 下にクローンする。
  ```
  git clone https://github.com/zsh-users/PLUGIN_NAME.git ~/.oh-my-zsh/custom/plugins/PLUGIN_NAME
  ```
- `~/.zshrc` 内の`plugins` の値に記載。
- `source ~/.zshrc` かターミナル再起動で反映

◾️ 実際に導入したプラグイン
- 公式
  - [aliases](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/aliases)
  - [copypath](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copypath)
  - [history](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/history)
  - [docker](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/docker)
  - [github](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/github)
  - [composer](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/composer)
  - [laravel](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/laravel)
  - [brew](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/brew)
  - （入れたはいいけどコマンド覚えられないし、使いこなせなさそう）
- zsh-users
  - [zsh-completions](https://github.com/zsh-users/zsh-completions):
    - コマンド入力から予測し補完をかけてくれる。
    ```
    git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
    ```
  - [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
    - コマンド履歴から補完をかけてくれる。
    ```
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```
  - [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
    - 入力をハイライトしてくれる
    ```
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```
- zshrc への記載
  ```
  plugins=(git aliases copypath history docker github composer laravel brew zsh-completions zsh-autosuggestions zsh-syntax-highlighting)
  ```




## おわりに
便利なものはもっと積極的に取り入れて作業効率を上げていこうと思った。

## 参考資料
- [公式ドキュメント](https://github.com/ohmyzsh/ohmyzsh)
- [公式プラグイン](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins-Overview)
- [チートシート](https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet)
- [zsh-users](https://github.com/zsh-users)
- [Oh My ZSH!便利ツールがあれば開発しやすい！](https://qiita.com/Oukaria/items/6cd0706beece722cd3db)
- [【mac】oh-my-zsh で iterm2 の見た目を整える](https://zenn.dev/sdutio_terrace/articles/4d9547d0fce01e)
