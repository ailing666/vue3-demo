<template>
  <div id="son">
    <h1>子组件</h1>
    {{ num }}
    <button @click="changeNum">changeNum</button>
  </div>
</template>

<script>
export default {
  name: 'Son',
  // 接收父组件传的参数
  props: {
    num: {
      type: Number,
      default: 0
    }
  },
  // 子组件触发父组件的方法
  setup (props, { emit }) {
    const changeNum = () => {
      emit('changeNum', props.num)
    }
    return { changeNum }
  }
}
</script>
