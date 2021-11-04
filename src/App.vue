<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { reactive } from '@vue/reactivity'
import Choices from './components/Choices.vue'

const choiceList = reactive([
  {
    date: '2021-10-04',
    name: 'カップ麺'
  },
  {
    date: '2021-10-05',
    name: 'マクドナルド'
  }
])
function addItem(name: string) {
  choiceList.push({
    date: '2021-10-02',
    name: name
  })
}
</script>

<template>
  <h1>ふーちょ！</h1>
  <p>今日のご飯なにする？アプリ</p>
  <!-- 選択肢部分 -->
  <Choices :list="choiceList" v-on:add="addItem" />
  <!-- ルーレット部分 -->
  <!-- ログ部分 -->
</template>

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
