<template>
  <h1>ふーちょ！</h1>
  <p>今日のご飯なにする？アプリ</p>
  <!-- 選択肢部分 -->
  <Choices :list="state.choiceList" @add="addItem" />
  <!-- ルーレット部分 -->
  <!-- ログ部分 -->
</template>

<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import dayjs from 'dayjs';
import { onMounted } from 'vue'
import { reactive } from '@vue/reactivity'
import Choices from './components/Choices.vue'

const state = reactive({
  choiceList: []
})

onMounted(()=> {
  state.choiceList = JSON.parse(localStorage.getItem('choices'))
})

const addItem = (name: string) => {
  const now = dayjs()
  state.choiceList.push({
    created: now.format('YYYY-MM-DD'),
    name: name
  })
  saveChoices()
}

const saveChoices = () => {
  const parsed = JSON.stringify(state.choiceList)
  localStorage.setItem('choices', parsed)
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
