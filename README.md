# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## Setup
### Install bundler
```
gem update bundler
gem install bundler
```
### Update ruby by rbenv
```
brew update
brew install rbenv ruby-build
```
Create path to rbenv
>[[ -d ~/.rbenv  ]] && \  
  export PATH=${HOME}/.rbenv/bin:${PATH} && \  
  eval "$(rbenv init -)"

```
# Check the version which we can install
rbenv install -l

# Install latest version
rbenv install 2.2.5

# Set the ruby as global
rbenv global 2.2.5

# Check the version
ruby -v

# Check the version by rbenv
rbenv versions
```

### Make users execute rails command
If you encounter this error,
>gem install rails  
ERROR:  While executing gem ... (Errno::EACCES)  
    Permission denied @ rb_sysopen -   /Users/nishina/.rbenv/versions/2.2.5/lib/ruby/gems/2.2.0/gems/rails-5.0.0.1/README.md

execute this command
```
# update Ruby

# Create symbolic link from system field to user field
ln -s /usr/bin/rails /usr/local/bin/rails
```

/usr/bin以下はシステムユーザーが利用できるディレクトリ.  
/usr/local/binにシンボリックリンクを貼ることでsudoをしなくてもgemを実行することができる。

### nokogiriに依存するインストールエラーについて
capybaraをインストールする際にnokogiriがインストールできないというエラーがでた。  
これはgemで管理されているnokogirinのバージョンとcapybaraが利用するnokogiriのバージョンに差があるから（な気がする)。以下の方法で対応
```
# 一旦nokogiriをアンインストール(必要ないかも)
$ gem uninstall nokogiri

# 削除されているか確認
$ gem list | grep nokogiri

# 必要なライブラリのインストール
$brew install libxml2 libxslt

# ライブラリのリンクを作成
$brew link libxml2 libxslt --force

# 以下のコマンドで実行(./bin/bundle実行時のエラーログを参考)
$gem install nokogiri -- --use-system-libraries

# 再実行
./bin/bundle

# nokogiriがインストールされているか確認
$gem list | grep nokogiri
```

[ここ](http://qiita.com/maangie/items/5f6a7885ec977e35552d)を参考にすると、もしかしたら以下のコマンドだけで十分だったかもしれない
```
% brew install libxml2
% NOKOGIRI_USE_SYSTEM_LIBRARIES=1 bundle update
```

### Intellij setting
* Set SDK
  * File -> Project Structure ... -> Project Settings -> Project  
