<template>
  <div id="app">
    <div>{{name}}---{{age}}</div>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue';
export default {
  setup() {
    // 定义一个响应式的对象
    const obj = reactive({
      name: 'loveZero',
      age: 666 
    })
    // 直接解构不是响应式的数据
    const { name } = obj
    console.log('name: ', name);
    console.log('obj: ', obj);
    // 将响应式对象中的所有值都转为响应式数据
    const obj2 = toRefs(obj)
    console.log('obj2: ', obj2);
    // 解构后，仍然是响应式的
    const { age } = obj2
    console.log('age: ', age);
    const btnClick = () =>{
      // 修改值不需要value
      obj.age += 1
      obj.name = 'hello'
    }
    // 函数
    return {
      ...obj2, // 将对象展开，模板中可直接用属性
      btnClick
    }
  },
}

</script>
