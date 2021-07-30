<template>
  <div id="app">生命周期</div>
</template>

<script>
import { onBeforeMount, onMounted } from 'vue'
export default {
  name:'App',
  setup(){
    /**
     * setup 创建实例前
     * onBeforeMount  挂载DOM前
     * onMounted 挂载DOM后
     * onBeforeUpdate 更新组件前
     * onUpdated 更新组件后
     * onBeforeUnmount 卸载销毁前
     * onUnmounted  卸载销毁后
     */
    console.log('setup---起点',this,document.getElementById('app'))
    onBeforeMount(()=>{
      console.log('onBeforeMount---DOM渲染前',this,document.getElementById('app'))
    })
    onMounted(()=>{
      console.log('onMounted---DOM渲染后1',this,document.getElementById('app'))
    })
    onMounted(()=>{
      console.log('onMounted---DOM渲染后2',this,document.getElementById('app'))
    })
  }
}

</script>