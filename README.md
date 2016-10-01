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
rbenv install 2.2.3

# Set the ruby as global
rbenv global 2.2.3

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

### Intellij setting
* Set SDK
  * File -> Project Structure ... -> Project Settings -> Project  
