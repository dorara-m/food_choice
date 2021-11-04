<script lang="ts">
import { ref } from 'vue'

export default {
  props: {
    list: { default: [] }
  },
  setup() {
    const input = ref('')

    // function addChoice() {
    //   // alert(input.value)
      
    // }

    return {
      input,
      // addChoice
    }
  }
}
</script>

<template>
  <!-- 一応選択肢出す -->
  <ul>
    <li v-for="item,index in list" :key="index">
      {{ item.name }}
    </li>
  </ul>
  <input type="text" v-model="input" placeholder="新規追加">
  <button @click="$emit('add', input.value)">追加</button>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
