<template>
  <div id="app">
    <div>{{obj.num}}---{{obj.age}}</div>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
import { reactive } from 'vue';
export default {
  setup() {
    // 当明确的知道需要的是一个响应式对象时，就是用reactive
    // 定义一个响应式的对象，复杂数据类型 
    const obj = reactive({
      name:'loveZero',
      age:666 
    })
    const btnClick = () =>{
      obj.age+=1
      obj.name = 'hello'
    }
    // 函数
    return {
      obj, // 模板中使用需返回，对象格式   
      btnClick
    }
  },
}

</script>
