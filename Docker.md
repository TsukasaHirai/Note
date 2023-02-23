# Docker

作業中

C:\Program Files\Common Files\Oracle\Java\javapath

- Docker Hubとは

  https://hub.docker.com/

ユーザーが作成したコンテナをアップロードして公開・共有できるサービス

基本的には公式のものを使おう



## コマンド詳細

| コマンド  | 意味                         | 例                         |
| --------- | ---------------------------- | -------------------------- |
| image     | イメージを対象にしたコマンド | docker image pull xxx      |
| container | コンテナを対象にしたコマンド | docker container start xxx |

- pull

  

## アプリケーション起動

- Webサーバー起動

  - nginx

    nginxインストール

    ```
    docker pull nginx
    ```

    nginx起動

    ```
    docker --name nginx -d -p 8080:80 nginx
    ```

  - postgres

    postgresインストール

    ```
    docker pull postgres
    ```

    postgres起動

    パスワードの設定などが必要になってくる

    ```
    docker run --name postgres -e POSTGRES_PASSWORD=password -e POSTGRES_INITDB_ARGS="--encoding=UTF8 --no-locale" -e TZ=Asia/Tokyo -v postgresdb:/var/lib/postgresql/data -p 9080:80 -d postgres
    ```

    

## 作業中

- ネットワーク作成

  ```
  docker network create wordpressnet1
  ```

  