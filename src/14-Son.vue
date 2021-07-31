<template>
  <div class="container">
    <h2>
      子组件 {{ modelValue }} <button @click="btnClick">改变modelValue</button>
    </h2>
  </div>
</template>
<script>
export default {
  name: 'Son',
  props: {
    // 子组件用  modelValue 接收
    modelValue: {
      type: Number,
      default: 0
    }
  },
  setup (props, { emit }) {
    const btnClick = () => {
      // 改变数据, 将参数赋值
      emit('update:modelValue', 100)
    }
    return { btnClick }
  }
}
</script>
