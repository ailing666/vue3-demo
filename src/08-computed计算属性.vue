<template>
  <div id="app">
    <div>字符串---{{ str }}</div>
    <div>反转后---{{ newStr }}</div>
  </div>
</template>

<script>
import { computed, ref } from 'vue'
export default {
  name: 'App',
  setup () {
    const str = ref('hello')
    // 计算属性：根据一定的逻辑得到一个新的数据，且是响应式的
    const newStr = computed(() => {
      // 返回新的数据
      return str.value
        .split('')
        .reverse()
        .join('')
    })
    return {
      str,
      newStr
    }
  }
}
</script>
