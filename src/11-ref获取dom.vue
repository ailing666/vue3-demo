<template>
  <div id="app">
    <!-- 单个dom -->
    <div ref="dom">box</div>
    <!-- 循环dom -->
    <ul>
      <li v-for="i in 5" :key="i" :ref="getDom">第{{ i }}个</li>
    </ul>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue'
export default {
  name: 'App',
  setup () {
    // 获取单个dom
    const dom = ref(null)
    onMounted(() => {
      console.log(dom.value)
    })

    // 获取多个dom
    const domList = []
    const getDom = el => {
      domList.push(el)
    }
    onMounted(() => {
      console.log(domList)
    })

    return {
      dom,
      getDom
    }
  }
}
</script>
