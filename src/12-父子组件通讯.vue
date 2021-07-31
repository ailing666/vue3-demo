<template>
  <div id="app">
    <h1>父组件</h1>
    {{ num }}
    <hr />
    <!-- 组件传参 -->
    <Son :num="num" @changeNum="changeNum"></Son>
  </div>
</template>

<script>
import Son from './12-Son.vue'
import { ref } from 'vue'
export default {
  name: 'App',
  components: { Son },
  setup () {
    const num = ref(10)
    const changeNum = val => {
      num.value += val
    }
    return { num, changeNum }
  }
}
</script>
