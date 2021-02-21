# Rails Tips

[Rubyのセットアップ](ruby.md)が完了していること

## プロジェクトの作成

### rails new

```bash
rails new [project name]
```
|オプション         |効果                                                 |
|:---------------:|:--------------------------------------------------:|
|ｰB, --skip-bundle|Railsプロジェクト作成時にbundle installを行わないようにする|
|--skip-turbolinks|turbolinksのセットアップをスキップ。                     |
|-d, --database   |データベースエンジンを変える。                           |

### solargraph bundle

ドキュメントの生成

```bash
cd [project name]
solargraph bundle
```

## 参考文献

- https://qiita.com/yuitnnn/items/b45bba658d86eabdbb26
- https://qiita.com/shinkuFencer/items/e6b4e24a92f7b34e9f24
