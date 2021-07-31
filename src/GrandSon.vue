<template>
  <div>
    <h1>孙组件</h1>
    {{ num }}
    <button @click="grandClick">grandClick</button>
  </div>
</template>

<script>
import { inject } from 'vue'
export default {
  name: 'Son',
  // 子组件触发父组件的方法
  setup () {
    const num = inject('num')
    const changeNum = inject('changeNum')
    const grandClick = () => {
      changeNum(12)
    }
    return { num, grandClick }
  }
}
</script>
