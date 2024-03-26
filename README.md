# devcontainer template

gitを使用するためのコンテナのテンプレートとして

## wsl(or ubuntu)側での処理

コンテナに`.ssh`と`.gitconfig`をマウントさせることで、wslでの設定を引き継ぐことができる

```sh
$ sudo apt install git
$ ssh-keygen -t ed25519
$ git config --global user.name " {GitHubのアカウント名} "
$ git config --global user.email " {GitHubに登録しているメールアドレス} "
```

## 現状インストールされるライブラリ
- ipykernel==6.26.0
- matplotlib==3.8.1
- numpy==1.26.1
- scikit-learn==1.3.2
