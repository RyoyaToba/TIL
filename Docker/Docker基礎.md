## Dockerとは

![Docker概要](https://github.com/RyoyaToba/TIL/blob/main/documents/architecture.svg)

https://matsuand.github.io/docs.docker.jp.onthefly/get-started/overview/

[参考 Youtube動画](https://www.youtube.com/watch?v=lZD1MIHwMBY&ab_channel=%E3%81%A0%E3%82%8C%E3%81%A7%E3%82%82%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%8B%E3%82%A2%2F%E5%B1%B1%E6%B5%A6%E6%B8%85%E9%80%8F)

Dockerはコンテナと呼ばれる仮想化のための技術。共同開発や既存のプロジェクトなどに参入する時、１人１人の使用しているPCの環境が異なる場合、実行環境の構築に多大な時間を要する。
Dockerはライブラリのアップデートや新しい変更をPCに加えることをすることなく、Immutable Infrastructureというアプローチにより環境構築を実現する。

Dockerには、Docker fileやDocker Imageという機能が標準で備わっており、それを用いて共通の環境構築を可能としている。

開発では、dockerHubから、イメージを持ってきて、ローカル上でその環境を構築できる

実行の流れ
1. クライアントが実行（docker run）
2. docker デーモンがレジストリからイメージを取得
3. イメージからコンテナを作成
4. コンテナを起動
