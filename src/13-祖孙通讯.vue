<template>
  <div id="app">
    <h1>根组件</h1>
    {{ num }}
    <button @click="changeNum(val)">父组件方法</button>
    <hr />
    <!-- 组件传参 -->
    <Son></Son>
    <hr />
    <GrandSon></GrandSon>
  </div>
</template>

<script>
import Son from './Son.vue'
import GrandSon from './GrandSon.vue'
import { ref, provide } from 'vue'
export default {
  name: 'App',
  components: { Son, GrandSon },
  setup () {
    const num = ref(10)
    // 共享num
    provide('num', num)
    const changeNum = (val = 1) => {
      num.value += val
    }
    // 共享changeNum方法
    provide('changeNum', changeNum)
    return { num, changeNum }
  }
}
</script>
