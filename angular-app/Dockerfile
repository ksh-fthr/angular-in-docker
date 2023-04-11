# -----------------------------------------------------
# Angular アプリをビルドするための環境を構築する
# -----------------------------------------------------
# Angualr のビルドする環境として node をインストール
# 12.18.3 は開発で使用しているバージョン
FROM node:14.21.3 as build-stage

WORKDIR /app
COPY ./app/package*.json /app/

# npm install 中に下記 Warning がでるが回避策が現状見当たらないので放置するしかない
# 内容はプラットフォームが Mac OSX ではないからスキップするというもので、
# 対象となっている fsevents は node_modules 中のライブラリが依存関係で使用しているライブラリ

# Warning の内容
#   npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.6 (node_modules/fsevents):
#   npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.6: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

RUN npm install
COPY ./app/ /app/
ARG configuration=production

# Angular アプリをビルドする
RUN npm run build -- --output-path=./dist/out --configuration $configuration

# -----------------------------------------------------
# Nginx の Docker 環境を構築する
# -----------------------------------------------------
FROM nginx:1.24

# ビルドした成果物を Docker 上の Nginx のドキュメントとして扱うためにコピー(デプロイ)
COPY --from=build-stage /app/dist/out/ /usr/share/nginx/html

# Nginx の設定ファイルを Docker 上の Nginx にコピー
COPY ./docker/nginx/nginx.conf /etc/nginx/nginx.conf

