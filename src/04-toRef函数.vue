<template>
  <div id="app">
    <div>{{name}}---{{age}}</div>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
import { reactive,toRef } from 'vue';
export default {
  setup() {
    // 定义一个响应式的对象
    const obj = reactive({
      name:'loveZero',
      age:666 
    })
    // 不需要整个响应式对象，只将其中要用的值保留出去
    const name = toRef(obj,'name')
    // 解构出来的属性不是响应式的
    let { age } = obj
    console.log('age: ', age);
    console.log('name: ', name);
    const btnClick = () =>{
      age += 1
      name.value = 'hello'
    }

    // 函数
    return {
      name,
      age,
      btnClick
    }
  },
}

</script>
