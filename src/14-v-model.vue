<template>
  <div id="app">
    <h1>父组件</h1>
    {{ count }}
    <hr />
    <!-- $event就是emit传的参数 -->
    <!-- <Son :modelValue="count" @update:modelValue="count = $event" /> -->
    <!-- v-model语法糖 -->
    <Son v-model="count" />
  </div>
</template>

<script>
import Son from './14-Son.vue'
import { ref } from 'vue'
export default {
  name: 'App',
  components: { Son },
  setup () {
    const count = ref(10)

    return { count }
  }
}
</script>
