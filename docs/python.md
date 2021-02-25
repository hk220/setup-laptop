# Pythonのセットアップ(deprecated)

## pyenvのインストール

```bash
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.profile
source ~/.profile
```

## python 3.9のインストール

```bash
pyenv install 3.9.2
pyenv global 3.9.2
```

## 参考文献

- https://github.com/pyenv/pyenv/blob/master/README.md
