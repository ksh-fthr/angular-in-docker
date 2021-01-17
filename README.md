# このプロジェクトについて
Docker + Angular + Nginx の環境構築を試したものです。
今後知見が増えたりアイディアが出たら更新することもあります。

# 環境について
以下の環境で実行・確認しています。

| 環境                                                         | バージョン              | 備考                         |
| ------------------------------------------------------------ | ----------------------- | ---------------------------- |
| macOS Catalina                                               | v10.15.7                |                              |
| [Docker Desktop for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac/) | v3.0.3                   | |
| Docker                                                       | v20.10.0, build 7287ab3 | `$ docker --version`         |
| Docker Compose                                               | v1.27.4, build 40524192 | `$ docker-compose --version` |
| [Angular CLI](https://cli.angular.io/)                       | v11.0.5                 | `$ ng --version`             |
| [Angular](https://angular.io/)                               | v11.0.5                 | 同上                         |
| [TypeScript](https://www.typescriptlang.org/)                | v4.0.2                  | 同上                         |
| [Node.js](https://nodejs.org/ja/)                            | v12.18.3                | `$ node --version`           |
| [npm](https://www.npmjs.com/)                                | v6.14.6                 | `$ npm --version`            |

<details>
<div>
<summary>Angular のバージョン詳細( ng version の結果 )</summary>

```bash
$ ng version

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/


Angular CLI: 11.0.5
Node: 12.18.3
OS: darwin x64

Angular: 11.0.5
... animations, cli, common, compiler, compiler-cli, core, forms
... platform-browser, platform-browser-dynamic, router
Ivy Workspace: Yes

Package                         Version
---------------------------------------------------------
@angular-devkit/architect       0.1100.5
@angular-devkit/build-angular   0.1100.5
@angular-devkit/core            11.0.5
@angular-devkit/schematics      11.0.5
@schematics/angular             11.0.5
@schematics/update              0.1100.5
rxjs                            6.6.0
typescript                      4.0.2
```

</div>
</details>


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

