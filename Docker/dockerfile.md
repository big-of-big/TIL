## Dockerfileからイメージをビルドする

```
docker build -t <name>:<tag> .
```

`-t`で名前をつける。名前がないイメージはダングリングイメージと言う。

## レイヤーについて
- Docker imageのレイヤー数は最小限にする
- レイヤーを作るのはRUN, COPY, ADD
- コマンドは&&でつなぐ
- \で改行する

## パッケージのインストール
新しいパッケージリストを取得してから
```
apt-get update
```

これを実行`apt-get install <package>`
