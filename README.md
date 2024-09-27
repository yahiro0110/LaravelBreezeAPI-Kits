# Laravel Breeze API Kits

## Outline

PHP のフレームワーク Laravel Breeze API の環境キットです。

## Requirement

-   nginx: latest
-   php: 8.1.0
-   MySQL: 8.0.26
-   Laravel 10

## Setup Instructions

1.  リポジトリをクローンします。

    ```bash
    git clone https://github.com/yahiro0110/LaravelBreezeAPI-Kits.git
    ```

2.  クローンしたディレクトリに移動します。

    ```bash
    cd LaravelBreezeAPI-Kits
    ```

3.  バックエンド環境変数用のファイルを用意します。

    ```bash
    cp ./api/.env.example ./api/.env
    ```

4.  .env ファイル内のデータベース接続設定、フロントの URL を追記します。

    ```markdown
    DB_CONNECTION=mysql
    DB_HOST=db
    DB_PORT=3306
    DB_DATABASE=mysql_test_db
    DB_USERNAME=admin
    DB_PASSWORD=secret

    FRONTEND_URL=http://localhost:3000
    ```

5.  Docker コンテナを起動します。

    ```bash
    docker compose up -d --build
    ```

6.  PHP コンテナへアクセスし、Laravel 環境設定の準備をします。

    ```bash
    # PHPコンテナにアクセス
    docker compose exec php bash

    # Laravel の依存関係をインストール
    composer update

    # アプリケーションキーの生成
    php artisan key:generate

    # データベーステーブルの作成
    php artisan migrate
    ```

7.  以下の URL にアクセスし、Json 形式の値が表示されるのを確認します。

    http://localhost:8000/

## Connection

1. PhpMyAdmin

    http://localhost:8081/

    DB 関連の情報を閲覧できます。

2. MailHog

    http://localhost:8025/

    mail に MailHog を使用しています。
