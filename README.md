
# Laravel7 の認証機能付きDocker-compose

<p align="center"><img src="https://res.cloudinary.com/dtfbvvkyp/image/upload/v1566331377/laravel-logolockup-cmyk-red.svg" width="400"></p>

## gitクローン
```
$ git clone git@github.com:yoshis2/laravel7-auth-docker-compose.git
$ cd laravel7-auth-docker-compose
```

## アプリ起動
```
$ docker-compose up -d --build
```

## web-appの設定
```
$ docker-compose exec web-app composer install
$ docker-compose exec web-app cp .env.example .env
$ docker-compose exec web-app php artisan key:generate
$ docker-compose exec web-app php artisan migrate
```
## npmの設定
nodeのdockerは起動していないので起動してインストール、ビルドする方法を取る  
nodeのステータスは [Exit 0]の状態ですが気にしないでください
```
$ docker-compose run node npm install
$ docker-compose run node npm run dev
```


## 動作確認
http://localhost:82/

## 参照
https://readouble.com/laravel/7.x/ja/authentication.html

## authのインターフェース
初期はVueによるレイアウトになっています。

こちらのコマンドでreactに変更できます。
'''
$ docker-compose exec web-app php artisan ui react --auth
'''

こちらのコマンドでbootstrapに変更できます。
'''
$ docker-compose exec web-app php artisan ui bootstrap --auth
'''
