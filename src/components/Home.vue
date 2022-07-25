<script setup>
import { ref } from 'vue'
import { store } from './store'


</script>

<template>
  <h1>Kana Kuizu</h1>

  <div v-show="store.kana_visible">
    <button type="button" @click="store.kana_visible = !store.kana_visible">start quiz</button>
  </div>
</template>

<style scoped>

</style>
