# Rails Tips

[Rubyのセットアップ](ruby.md)が完了していること

## プロジェクトの作成

```bash
rails new [project name] -B
```
|オプション         |効果                                                 |
|:---------------:|:--------------------------------------------------:|
|ｰB, --skip-bundle|Railsプロジェクト作成時にbundle installを行わないようにする|

## vender/bundle以下にgemをインストールする

vender/bundle以下にgemをインストールすることで、solargraphといったツールでgemの中のコードにジャンプできるようになる。

```bash
bundle install --path vendor/bundle
```

## 参考文献

- https://qiita.com/yuitnnn/items/b45bba658d86eabdbb26
