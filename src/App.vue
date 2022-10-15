<script setup>
import Home from './components/Home.vue'
import Kana from './components/Kana.vue'
import Results from './components/Results.vue'
import { store } from './components/store'

</script>

<template>
  <div v-if="store.home_visible">
    <Home/>
  </div>

  <div v-if="store.kana_visible">
    <Kana/>
  </div>

  <div v-if="store.results_visible">
    <Results/>
  </div>
  

</template>

<style scoped>

</style>
