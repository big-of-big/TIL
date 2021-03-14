# slot
slotを使うことで親から子へHTMLを渡すことができる
## 基本
```
--------------この2行がslotタグになる----------------
<p>HelloWorld!!!!</p>
<p>親の数：{{ num }}</p>
-----------------------------------------------------
```

親コンポーネント
```vue
<template>
  <div id="app">
    <button @click="num++">+1ボタン</button>
    <HelloWorld>
      <p>HelloWorld!!!!</p>
      <p>親の数：{{ num }}</p>
    </HelloWorld>
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
  }
}
</script>
```

子コンポーネント
```vue
<template>
  <div class="hello">
    <p>これは子コンポーネント</p>
    <slot></slot>
    <slot></slot>
    <slot></slot>
  </div>
</template>
```
