<script setup>
import { store } from './store';
import sakura from '../assets/sakura.jpeg';

let kana_correct = store.correct_count;
let kana_count  = store.kana_count;
let emote = '';

if (kana_correct === kana_count) {
    emote = 'Perfect!';
} else if (kana_correct > kana_count/2) {
        emote = 'Well done, you answered most correctly. Keep going!';
} else { 
    emote = 'Keep practicing, you\'ve got this!';
}

function home() {
    store.results_visible = !store.results_visible;
    store.home_visible = !store.home_visible;

    store.kana_count = 0;
    store.correct_count = 0;
    store.mistake_count = 0;
}

</script>


<template>

<div class="results" :style="{'background-image': `url(${sakura})`}">
    <h1>Result<br>{{kana_correct}}/{{kana_count}}</h1>
    <p>{{emote}}</p>
    
    <div>
        <button @click="home">home</button>
    </div>

</div>

</template>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Nothing+You+Could+Do&family=Silkscreen&display=swap');
.results {
    display: grid;
    grid-template-rows: 200px 200px 200px;
    align-items: center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 100vh;
    color: #000;
}

h1 {
    font-family: 'Silkscreen', cursive;
    font-size: 2.5rem;
    font-weight: 400;
    margin: 0px; 
}

p {
    font-size: 1.8rem;
    font-weight: 200;
    /* max-width: 260px; */
    margin: auto;
    padding: 15px 10px;
    border-radius: 10px;
    background-color: rgba(234, 212, 221, 0.7);
}

@media (max-width: 500px) {
    p {
        max-width: 260px;
    }
}
</style>