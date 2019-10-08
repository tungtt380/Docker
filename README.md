事前準備
=============

以下をhostsに加える   

```
127.0.0.1 caruvi.local
```

開発環境の作成
=============

Docker の build
-------------

```bash
cd ./Docker
docker-compose build
docker-compose up -d
```

最初の作業
-------------

```bash
### WEBサーバーにログイン
docker-compose exec webmeishi bash

### laravel ディレクトリに移動
cd /var/www/vhost/caruvi.jp/laravel

### .env ファイル（設定ファイル）を作成
cp .env.example .env

### 依存ファイルをインストール
composer install

php artisan key:generate

php artisan jwt:secret

### DBを作成
php artisan migrate

npm install
```

Docker 操作（参考）
=============

```bash
### ドッカーを開始するとき
docker-compose start

### ドッカーを停止するとき
docker-compose stop

### WEBサーバーにログイン
docker-compose exec webmeishi bash

### DBサーバーにログイン
docker-compose exec mydb_meishi bash

### ドッカーの再作成
docker-compose down
docker-compose up
```
