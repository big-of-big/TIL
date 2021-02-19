## コンテナに入る
```
docker exec -it ID bash
```

## コンテナから出る
これをデタッチと言う。
```
ctrl p q
```
デタッチしたコンテナに入るには以下のコマンドを使う。
```
docker attach ID
```

### exitでも可能
exitとデタッチは挙動が異なる。

## イメージに別の名前をつけてコピーする
docker hubのリポジトリとイメージは同じ名前にする。
1つリポジトリが1つのイメージと対応する。
```
docker tag 元の名前 新しい名前
```

## バックグランドで動かす
```
docker run -d <image>
```

## コンテナをExit後に削除する（1回きりのコンテナ)
```
docker run --rm <image>
```

## docker startについて
このコマンドはimageにあるデフォルトのコマンドが実行される。
そのあとはExit状態になる。

## 停止中のコンテナを全削除
```
docker system prune
```
