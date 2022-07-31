<script setup>
import { store, options } from './store'

function select_option(i) {
  options.forEach(item => {
    item.selected = false;
  });

  options[i].selected = true;

  options.forEach(item => {
    if (item.selected === true) {
      item.color = '#34d399';
    } else {
      item.color = '#2b2d42';
    }
  });
  
}

function start_quiz() {
  store.home_visible = !store.home_visible;
  store.kana_visible = !store.kana_visible
}

</script>

<template>
  <h1>Kana Kuizu</h1>
  <div class="options-div" v-show="store.home_visible" v-for="(item, i) in options" :key="i">
    <div class="option" @click="select_option(i)" :style="{'background-color': options[i].color}" :key="i">
      <span>{{item.option}}</span>
      <span>{{item.kana}}</span>
    </div>
  </div>
  <div v-show="store.home_visible">
    <button type="button" @click="start_quiz">start quiz</button>
  </div>
</template>

<style scoped>
h1 {
  color: #2b2d42;
  font-weight: 200;
  font-size: 2.5rem;
}
h2 {
  color: #2b2d42;
  font-weight: 200;
  font-size: 2rem;
}
.options-div {
  display: flex;
  flex-direction: column;
  place-items: center;
  color: #fff;
  font-weight: 200;
  font-size: 1.8rem;
  gap: 10px;
  margin: 20px;
}
.option {
  display: flex;
  flex-direction: column;
  place-items: center;
  justify-content: space-evenly;
  background-color: #2b2d42;
  cursor: pointer;
  width: 320px;
  height: 150px;
  border-radius: 10px;
}
.option:hover {
  opacity: 0.9;
}
</style>
