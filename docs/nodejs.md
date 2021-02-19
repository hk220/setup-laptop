# Nodejsのセットアップ

## Nodejsのインストール

```bash
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add -

VERSION=node_14.x
DISTRO="$(lsb_release -s -c)"
echo "deb https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee /etc/apt/sources.list.d/nodesource.list
echo "deb-src https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee -a /etc/apt/sources.list.d/nodesource.list

sudo apt update
sudo apt install nodejs
```

## yarnのインストール

```bash
npm install --global yarn
```

## 参考文献

- https://github.com/nodesource/distributions/blob/master/README.md#manual-installation
- https://classic.yarnpkg.com/en/docs/install#debian-stable
