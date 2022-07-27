<script setup>
import { store, katakana, hiragana } from './store'
import { reactive, ref, onMounted} from 'vue';

let kana_list = reactive([...hiragana, ...katakana]);

function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
}

shuffle(kana_list);

const item_refs = ref([]);

function focus_next(i) {
    if (item_refs.value[i + 1] !== undefined) {
        item_refs.value[i + 1].focus();
    }
}

function check_input(input, romaji, i) {
    if (input === romaji) {
        kana_list[i].color = '#34d399';
        kana_list[i].disabled = true;
    } else {
        kana_list[i].color = '#2b2d42'
    }
    
    focus_next(i);
}

</script>

<template>
<div class="flex">
    <div class="grid" v-for="(item, i) in kana_list" :key="i" >
        <div class="kana" :style="{'background-color': kana_list[i].color}" >
            <span>{{item.kana}}</span>
            <input v-model="kana_list[i].input" :key="i" @keydown.enter="check_input(kana_list[i].input, item.romaji, i)" 
            :disabled="kana_list[i].disabled" ref="item_refs" autocapitalize="off"/>
        </div>
    </div>
</div>
<button @click="store.kana_visible = !store.kana_visible">done</button>
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
    width: 160px;
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
</style>