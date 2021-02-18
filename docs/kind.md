# kindのセットアップ

先に、[Dockerのセットアップ](docker.md)を済ませておくこと。

## インストール

```bash
sudo curl -L "https://kind.sigs.k8s.io/dl/v0.10.0/kind-linux-amd64" -o /usr/local/bin/kind
sudo chmod +x /usr/local/bin/kind
```

## create cluster

```bash
kind create cluster
```

## kubectlのインストール

```bash
sudo curl -L "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl" -o /usr/local/bin/kubectl
sudo chmod +x /usr/local/bin/kubectl
```

## 参考文献

- https://kind.sigs.k8s.io/docs/user/quick-start/
- https://kubernetes.io/ja/docs/tasks/tools/install-kubectl/
