# オブジェクト

- オブジェクトのプロパティは文字列orシンボル。
- プロパティ名が変数の命名規則通りなら`""`は省略できる。
- プロパティ名と値（変数）が同じなら省略記法が使える。
- オブジェクトのプロパティ名は暗黙的に文字列になる。

```javascript
const hoge = "hoge"
const obj = { hoge }
// { hoge: hoge }と同じ意味
```

## プロパティ名に変数を使いたい
```javascript
const hoge = "hoge"
const obj = { [hoge] : "val" }
```
