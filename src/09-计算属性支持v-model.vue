<template>
  <div id="app">
    <div>今年<input type="text" style="width:20px" v-model="nowAge" />岁</div>
    <div>后年<input type="text" style="width:20px" v-model="afterAge" />岁</div>
  </div>
</template>

<script>
import { computed, ref } from 'vue'
export default {
  name: 'App',
  setup () {
    const age = ref(0)
    // 计算属性传入对象可以支持v-model
    const nowAge = computed({
      get () {
        return age.value
      },
      set (val) {
        // 修改计算属性时触发
        afterAge.value = val - 2
      }
    })

    const afterAge = computed({
      get () {
        return age.value + 2
      },
      set (val) {
        age.value = val - 2
      }
    })
    return {
      nowAge,
      afterAge
    }
  }
}
</script>
