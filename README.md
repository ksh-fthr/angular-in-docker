# このプロジェクトについて
Docker + Angular + Nginx の環境構築を試したものです。
今後知見が増えたりアイディアが出たら更新することもあります。

# 環境について
以下の環境で実行・確認しています。

| 環境                                                         | バージョン              | 備考                         |
| ------------------------------------------------------------ | ----------------------- | ---------------------------- |
| macOS Catalina                                               | v10.15.7                |                              |
| [Docker Desktop for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac/) | v3.0.3                  |                              |
| Docker                                                       | v20.10.0, build 7287ab3 | `$ docker --version`         |
| Docker Compose                                               | v1.27.4, build 40524192 | `$ docker-compose --version` |

# ブランチについて
環境構築のためのプロジェクトなので、ブランチを切って修正することは考えていません。
`master` ブランチのみで更新を行う予定です。

# 動かし方
次のコマンドを実行することで `npm build` された Angular アプリが Docker + Nginx 上で動きます。
ご自身の開発環境で実行した場合は http://localhost にブラウザからアクセスすれば Docker 上で動いている Angular アプリが確認できます。
別の PC で実行している場合は http://ホストのIPアドレス にブラウザからアクセスしてください。
同じく Docker 上で動いている Angular アプリが確認できます。

```bash
$ docker-compose up -d --build
```

`-d` はバックグラウンドで動かすオプションです。
フォアグラウンドで動かしたい場合は `-d` をつけずに実行してください。

# 停め方
## サービスの停止
サービスは停止するが Docker コンテナは削除したくない場合は下記コマンドを実行してください。

```bash
$ docker-compose stop
```

## コンテナの停止
サービスの停止とサービスを提供するコンテナの削除、それからネットワークも削除したい場合は下記コマンドを実行してください。

```bash
$ docker-compose down
```

# 開発時の動作確認
Docker 上でビルドされたアプリを動かすのではなく、開発時の動作確認をしたい場合は次のコマンドを実行してください。

```bash
$ cd angular-app/app
$ ng serve
```

http://localhost:4200 にブラウザからアクセスすることで、動作確認ができます。

