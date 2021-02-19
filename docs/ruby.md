# Rubyのセットアップ

## rbenvのインストール

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
~/.rbenv/bin/rbenv init >> ~/.profile
source ~/.profile
```

## ruby-buildのインストール

```bash
sudo apt-get install -y autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
```

## ruby 2.7.2のインストール

```bash
rbenv install 2.7.3
```

## 参考文献

- https://github.com/rbenv/rbenv#installing-ruby-versions
- https://github.com/rbenv/ruby-build/wiki
- https://qiita.com/ma2shita/items/5c41aa8a4908c919ba78
