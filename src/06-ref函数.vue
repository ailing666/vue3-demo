<template>
  <div id="app">
    <div>{{name}}---{{age}}</div>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    // 需要什么数据就定义什么数据，简单类型
    const name = ref('loveZero')
    console.log('name: ', name);
    const age = ref(18)
    const btnClick = () =>{
      // 修改值需要value
      age.value += 1
      name.value = 'hello'
      foo()
    }
    return {
      name,
      age,
      btnClick
    }  
  },
}

</script>
