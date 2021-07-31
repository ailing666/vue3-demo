<template>
  <div id="app">
    <!-- 单个dom -->
    <div ref="dom">box</div>
    <!-- 循环dom -->
    <ul>
      <li v-for="i in count" :key="i" :ref="getDom">第{{ i }}个</li>
    </ul>
    <button @click="count++">{{ count }}</button>
    <button @click="logList">logList</button>
  </div>
</template>

<script>
import { onMounted, onBeforeUpdate, ref } from 'vue'
export default {
  name: 'App',
  setup () {
    // 获取单个dom
    const dom = ref(null)
    onMounted(() => {
      console.log(dom.value)
    })

    // 获取多个dom
    let domList = []
    const getDom = el => {
      domList.push(el)
    }
    onMounted(() => {
      console.log(domList)
    })
    // 在更新前，将list清空
    onBeforeUpdate(() => {
      domList = []
    })

    let count = ref(4)

    const logList = () => {
      console.log(domList)
    }
    return {
      count,
      dom,
      getDom,
      logList
    }
  }
}
</script>
