## watchについて
`computed`に記載した関数ははHTMLに無いと実行されることはない。
HTMLに書く必要は無いが、dataが変更されたら任意の関数を実行したいときにwatchが使える。
具体的にはdataに書いた名前と同じ名前の関数名をwatchの中に書く。

```javascript
data: {
  name: '',
  number: 0
},
watch: {
  name() {
  # nameが変更されたらする処理
  },
  number() {
    # 同上
  }
}
```

[Vue\.js入門 \(7\) ウォッチャ \| Hypertext Candy](https://www.hypertextcandy.com/vuejs-introduction-watcher)
