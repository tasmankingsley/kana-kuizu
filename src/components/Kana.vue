<script setup>
import { store, options, hiragana, katakana } from './store'
import { reactive, ref } from 'vue';

let kana_list = reactive([]);
const item_refs = ref([]);

function populate_list() {
    if (options[0].selected === true) {
        kana_list = [...hiragana];
    } else if (options[1].selected === true) {
        kana_list = [...katakana];
    } else if (options[2].selected === true) {
        kana_list = [...hiragana, ...katakana];
    }
}

function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
}

function focus_next(i) {
    if (item_refs.value[i + 1] !== undefined) {
        item_refs.value[i + 1].focus();
    }
}

function check_input(input, romaji, i) {
    if (input === romaji) {
        kana_list[i].color = '#34d399';
        kana_list[i].disabled = true;
        store.correct_count++;
    } else {
        kana_list[i].color = '#2b2d42'
        store.mistake_count++;
    }
    
    focus_next(i);
}

function reset_array() {
    kana_list.forEach(element => {
        element.input = '';
        element.color = '#000';
        element.disabled = false;
    });
}

function done() {
    store.kana_visible = !store.kana_visible;
    store.results_visible = !store.results_visible;

    reset_array();
    shuffle(kana_list);

    store.kana_count = kana_list.length;
}

function back() {
    store.kana_visible = !store.kana_visible;
    store.home_visible = !store.home_visible;

    reset_array();
    shuffle(kana_list);

    store.kana_count = 0;
    store.correct_count = 0;
    store.mistake_count = 0;
}

populate_list();
shuffle(kana_list);

</script>

<template>
<button class="back" @click="back">＜</button>
<div class="flex">
    <div class="grid" v-for="(item, i) in kana_list" :key="i" >
        <div class="kana" :style="{'background-color': kana_list[i].color}" >
            <span>{{item.kana}}</span>
            <input v-model="kana_list[i].input" :key="i" @keydown.enter="check_input(kana_list[i].input, item.romaji, i)" 
            :disabled="kana_list[i].disabled" ref="item_refs" autocapitalize="off"/>
        </div>
    </div>
</div>
<button @click="done">done</button>
</template>

<style scoped>
.flex {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-evenly;
    gap: 20px;
    margin: 20px;
}

.kana {
    display: flex;
    flex-direction: column;
    place-content: center;
    place-items: center;
    width: 150px;
    height: 180px;
    font-size: 4rem;
    border-radius: 10px;
    opacity: 0.9;
}

input {
    font-size: 2rem;
    width: 100px;
    text-align: center;
    border-radius: 5px;
    border-style: none;
}

button {
    margin: 20px;
}

.back {
    position: absolute;
    left: 0px;
    top: 0px;
    padding: 5px 10px;

}
</style>