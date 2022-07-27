<script setup>
import Home from './components/Home.vue'
import Kana from './components/Kana.vue'
import { store } from './components/store'

</script>

<template>
  <Home/>
  <div v-if="store.kana_visible">
    <Kana/>
  </div>
  

</template>

<style scoped>

</style>
