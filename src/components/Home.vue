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
h1 {
  color: #2b2d42;
  font-weight: 200;
  font-size: 2.5rem;
}

</style>
