<template>
  <!-- 一応選択肢出す -->
  <ul class="choice_list">
    <li v-for="item,index in list" :key="index">
      {{ item.name }}
    </li>
  </ul>
  <input type="text" v-model="input" placeholder="新規追加">
  <button @click="addChoice">追加</button>
</template>

<script lang="ts">
import { ref } from 'vue'

export default {
  props: {
    list: { default: [] }
  },
  emits: ['add'],
  setup(props, context) {
    const input = ref('')

    const addChoice = () => {
      context.emit('add', input.value)
      input.value = ''
    }

    return {
      input,
      addChoice
    }
  }
}
</script>

<style scoped>
.choice_list {
  margin-top: 30px;
}
</style>
