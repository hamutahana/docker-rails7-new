## dockerコンテナ生成手順
```bash
# dockerイメージを生成
docker-compose build

# dockerコンテナを生成・起動
docker-compose up
```


## docker-rails7環境の作成手順
```bash
# ディレクトリの作成
mkdir [directory_name]

# ディレクトリに移動
cd [directory_name]

# Ruby3.2.2がインストールされたコンテナを起動してシェルを起動
# Macの場合
docker run --rm -ti -v ./rails-practice:/app ruby:3.2.2-alpine sh
# Windowsの場合
docker run --rm -ti -v "$(pwd)/boards:/app" ruby:3.2.2-alpine sh

# パッケージリストを更新する
apk update

# Railsでアプリケーションを作成する際に必要なパッケージをインストールする
apk add g++ make mysql-dev tzdata

# RubyGemシステム（gemそのもの）をアップデートする
gem update --system

# Railsのインストールバージョンを指定する
gem install rails -v 7.0.6

# プロジェクトを作成する
rails new /app --force --database=mysql --skip-bundle --skip-test
```

## アノテーション生成コマンド
```bash
# モデル作成後に以下のコマンドを実行する
docker-compose exec web bundle exec annotate --models
```