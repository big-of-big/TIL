# 親子間でデータを受け渡す
## 親から子へデータを渡す
親から子へデータを渡す時は`props`を使う

親コンポーネント
```javascript
<template>
  <div id="app">
    <p>親の数: {{ num }}</p>
    <button @click="num++">増やす</button>
# HelloWorldコンポーネント（子）へデータを渡している。
    <HelloWorld
      message="子に渡すメッセージ"
      :number="num" // v-bindを使うことで属性を動的にする
    />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  data() {
    return {
      num: 0
    }
  },
// nameはデバック用（無くても変わらない）
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>
```

子コンポーネント
```javascript
<template>
  <div class="hello">
    <p>親からもらったメッセージ：{{ message }}</p>
    <p>親からもらった半分の数：{{ halfNumber }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  // ここで親からもらっている
  props: {
    message: String,
    number: Number
  },
  computed: {
    halfNumber() {
      // このようにthisを使って親からもらったデータにアクセスできる
      return this.number / 2
    }
  },
  watch: {
    number() {
      console.log(this.number / 2)
    }
  }
}
</script>
```

## 子から親へデータを渡す
カスタムイベント名はケバブケースで書く。

親コンポーネント
```vue
<template>
  <div id="app">
    <p>親の数: {{ num }}</p>
    <button @click="num++">増やす</button>
    <HelloWorld
      message="子に渡すメッセージ"
      :number="num"
      @child-message="recevieMessage"
    />
    <pre>{{ $data }}</pre>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  data() {
    return {
      num: 0,
      message: ''
    }
  },
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    // valueには子コンポーネントの第二引数が入る（Vueが用意してくれている）
    // 引数の数を増やすことで複数の値を受け取ることができる。
    recevieMessage(value1,value2, val3) {
      console.log(value1, value2,val3, "子からメッセージがきたよ。")
      this.message = value1
    }
  }
}
</script>
```

子コンポーネント
```vue
<template>
  <div class="hello">
    <p>{{ message }}</p>
    <p>親からもらった半分の数：{{ halfNumber }}</p>
    <button @click="sendMessage">親にメッセージを送る</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      childMessage: '子のメッセージ',
    }
  },
  props: {
    message: String,
    number: Number
  },
  computed: {
    halfNumber() {
      return this.number / 2
    }
  },
  watch: {
    number() {
      console.log(this.number / 2)
    }
  },
  methods: {
    sendMessage() {
      // child-messageというイベントがあるよ。と親に送る。
      // HTMLは大文字と小文字を区別できないのでカスタムイベントはケバブケース(hoge-piyoスタイル)でかく。
      // 子コンポーネントの好きなタイミングで親のメソッドを呼び出すことができる。
      this.$emit('child-message', this.childMessage, 'hoge')
    }
  }
}
</script>
```
