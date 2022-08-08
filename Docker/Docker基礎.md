## Dockerとは

参考　　https://www.youtube.com/watch?v=lZD1MIHwMBY&ab_channel=%E3%81%A0%E3%82%8C%E3%81%A7%E3%82%82%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%8B%E3%82%A2%2F%E5%B1%B1%E6%B5%A6%E6%B8%85%E9%80%8F

アプリを簡単に開発、デプロイできる技術。環境構築が容易。テスト環境も本番環境も簡単に用意できる。

OS、ライブラリ、アプリケーションをひとまとまりにしたパッケージ。

イメージという雛形からコンテナを用意して、コンテナを起動している

デーモン：バックグラウンドで動く

実行の流れ
1. クライアントが実行（docker run）
2. docker デーモンがレジストリからイメージを取得
3. イメージからコンテナを作成
4. コンテナを起動

## dockerコマンド

## Docker fileを作る

Dockerfileの中には、ベースのファイルを指定し、その後でどんな作業をするかを記述していく。

## Docker Compose

複数のアプリケーションをまとめて操作

docker-compose.ymlに記述していく

### docker-compose build

イメージのビルド

### docker-compose up -d

コンテナの作成と起動

### docker-compose down

コンテナを停止

### docker-compose ps

コンテナ一覧を表示

### docker-compose run サービス名　コマンド

コンテナを作成してコマンドを実行

### docker-compose exec サービス名　コマンド

起動中のコンテナにコマンドを実行

