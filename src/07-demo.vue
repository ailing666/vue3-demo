<template>
  <div id="app">
    <div>{{ x }}---{{ y }}</div>
    <button @click="btnClick">点我增加{{ num }}</button>
  </div>
</template>

<script>
import { onMounted, onUnmounted, reactive, toRefs, ref } from 'vue'
// 记录鼠标位置方法
const useMouse = () => {
  // 响应式x，y坐标
  const mouse = reactive({
    x: 0,
    y: 0
  })
  // 鼠标移动方法
  const move = e => {
    mouse.x = e.pageX
    mouse.y = e.pageY
  }
  onMounted(() => {
    // DOM渲染完成，监听鼠标移动
    document.addEventListener('mousemove', move)
  })

  onUnmounted(() => {
    // 组件卸载销毁后，移除事件
    document.removeEventListener('mousemove', move)
  })
  return mouse
}
// 数字自增
const addNum = () => {
  // 响应式数字
  const num = ref(0)
  // 点击自增
  const btnClick = () => {
    num.value += 1
  }
  return { num, btnClick }
}
export default {
  setup () {
    const mouse = useMouse()
    const { num, btnClick } = addNum()
    return {
      ...toRefs(mouse),
      num,
      btnClick
    }
  }
}
</script>
