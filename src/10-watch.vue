<template>
  <div id="app">
    <div>ref数据：{{ num }} --- {{ name }}</div>
    <button @click="refClick">监听ref定义的响应式数据</button>
    <hr />
    <div>reactive数据：{{ id }}---{{ car }} --- {{ list[0].brand }}</div>
    <button @click="reactiveClick">监听reactive定义的响应式数据</button>
  </div>
</template>

<script>
import { ref, watch, reactive, toRefs } from 'vue'
export default {
  name: 'App',
  setup () {
    const num = ref(1)
    const name = ref('loveZero')
    const refClick = () => {
      num.value++
      name.value += num.value
    }

    watch(num, (newV, oldV) => {
      console.log('监听单个ref值')
      console.log('newV: ', newV, 'oldV: ', oldV)
    })

    watch([num, name], (newV, oldV) => {
      console.log('监听多个ref值')
      console.log('newV1: ', newV[0], 'oldV1: ', oldV[0])
      console.log('newV2: ', newV[1], 'oldV2: ', oldV[1])
    })

    const obj = reactive({
      id: 666,
      car: '车',
      list: [
        { id: 123, brand: '宝马' },
        { id: 124, brand: '奔驰' }
      ]
    })
    const reactiveClick = () => {
      obj.id = 999
      obj.car = '房'
      obj.list[0].brand = '大众'
    }

    // 监听
    watch(
      obj,
      val => {
        console.log('监听reactive')
        console.log('改变后的对象 ', val)
      },
      {
        // 默认触发
        immediate: true
      }
    )
    // 监听对象中某一个属性的变化
    watch(
      () => {
        obj.car
      },
      () => {
        console.log('监听reactive中某一个属性的变化')
        console.log('改变后的值 ', obj.car)
      },
      {
        // 开启深度监听
        deep: true
      }
    )
    return {
      ...toRefs(obj),
      num,
      name,
      refClick,
      reactiveClick
    }
  }
}
</script>
