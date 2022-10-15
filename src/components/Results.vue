<script setup>
import { store } from './store';

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
    <div>
        <h1>Result: {{kana_correct}}/{{kana_count}}</h1>
        <p>{{emote}}</p>
    </div>

<button @click="home">home</button>
</template>


<style scoped>
div {
    margin-top: 100px;
    margin-bottom: 100px;
    color: #000;
}

h1 {
    font-size: 2rem;
    font-weight: 400;  
}

p {
    font-size: 1.8rem;
    font-weight: 200;
}
</style>