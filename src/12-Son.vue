<template>
  <div id="son">
    <h1>子组件</h1>
    {{ num }}
  </div>
</template>

<script>
import { inject } from 'vue'
export default {
  name: 'Son',
  // 子组件触发父组件的方法
  setup () {
    const num = inject('num')
    return { num }
  }
}
</script>
