<!--  -->
<template>
  <div>
    <div>{{num}}</div>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
export default {
  /**
   * 组合API的起点
   * 可以理解为再beforeCreate钩子执行前执行，组件实例创建前
   * 不能使用this
   * 模板中需要使用功能的数据和函数，需要在setup中返回 
   */
  setup() {
    console.log('setup执行',this); // 无法使用this
    // 数据
    let num = 666
    const btnClick = () =>{
      console.log('btnClick');
    }
    // 函数
    return {
      num, // 模板中使用需返回，对象格式   
      btnClick
    }
  },
  beforeCreate() {
    console.log('beforeCreate执行');
  },
}

</script>
