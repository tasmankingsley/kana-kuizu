<script setup>
import { ref } from 'vue'
import { store } from './store'


</script>

<template>
  <h1 v-if="store.kana_visible">Kana Kuizu</h1>

  <div class="card">
    <button type="button" @click="store.kana_visible = !store.kana_visible">start quiz</button>
  </div>
</template>

<style scoped>

</style>
