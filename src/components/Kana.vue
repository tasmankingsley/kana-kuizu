<script setup>
import { store } from './store'
import { reactive, ref, onMounted} from 'vue';

let kana_list = reactive([
    {kana: 'ア', romaji: 'a', input: '', color: '#000', disabled: false},
    {kana: 'イ', romaji: 'i', input: '', color: '#000', disabled: false},
    {kana: 'ウ', romaji: 'u', input: '', color: '#000', disabled: false},
    {kana: 'エ', romaji: 'e', input: '', color: '#000', disabled: false},
    {kana: 'オ', romaji: 'o', input: '', color: '#000', disabled: false},
    {kana: 'カ', romaji: 'ka', input: '', color: '#000', disabled: false},
    {kana: 'キ', romaji: 'ki', input: '', color: '#000', disabled: false},
    {kana: 'ク', romaji: 'ku', input: '', color: '#000', disabled: false},
    {kana: 'ケ', romaji: 'ke', input: '', color: '#000', disabled: false},
    {kana: 'コ', romaji: 'ko', input: '', color: '#000', disabled: false},
    {kana: 'サ', romaji: 'sa', input: '', color: '#000', disabled: false},
    {kana: 'シ', romaji: 'shi', input: '', color: '#000', disabled: false},
    {kana: 'ス', romaji: 'su', input: '', color: '#000', disabled: false},
    {kana: 'セ', romaji: 'se', input: '', color: '#000', disabled: false},
    {kana: 'ソ', romaji: 'so', input: '', color: '#000', disabled: false},
    {kana: 'タ', romaji: 'ta', input: '', color: '#000', disabled: false},
    {kana: 'チ', romaji: 'chi', input: '', color: '#000', disabled: false},
    {kana: 'ツ', romaji: 'tsu', input: '', color: '#000', disabled: false},
    {kana: 'テ', romaji: 'te', input: '', color: '#000', disabled: false},
    {kana: 'ト', romaji: 'to', input: '', color: '#000', disabled: false},
    {kana: 'ナ', romaji: 'na', input: '', color: '#000', disabled: false},
    {kana: 'ニ', romaji: 'ni', input: '', color: '#000', disabled: false},
    {kana: 'ヌ', romaji: 'nu', input: '', color: '#000', disabled: false},
    {kana: 'ネ', romaji: 'ne', input: '', color: '#000', disabled: false},
    {kana: 'ノ', romaji: 'no', input: '', color: '#000', disabled: false},
    {kana: 'ハ', romaji: 'ha', input: '', color: '#000', disabled: false},
    {kana: 'ヒ', romaji: 'hi', input: '', color: '#000', disabled: false},
    {kana: 'フ', romaji: 'fu', input: '', color: '#000', disabled: false},
    {kana: 'ヘ', romaji: 'he', input: '', color: '#000', disabled: false},
    {kana: 'ホ', romaji: 'ho', input: '', color: '#000', disabled: false},
    {kana: 'マ', romaji: 'ma', input: '', color: '#000', disabled: false},
    {kana: 'ミ', romaji: 'mi', input: '', color: '#000', disabled: false},
    {kana: 'ム', romaji: 'mu', input: '', color: '#000', disabled: false},
    {kana: 'メ', romaji: 'me', input: '', color: '#000', disabled: false},
    {kana: 'モ', romaji: 'mo', input: '', color: '#000', disabled: false}
]);

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
            :disabled="kana_list[i].disabled" ref="item_refs" />
        </div>
    </div>
</div>
<button @click="store.kana_visible = !store.kana_visible">done</button>
</template>

<style scoped>
.flex {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    gap: 10px;
}
.grid {

}
.kana {
    display: flex;
    flex-direction: column;
    place-content: center;
    place-items: center;
    gap: 5px;
    width: 180px;
    height: 180px;
    font-size: 4rem;
    margin: 5px;
    /* background-color: #2b2d42; */
    border-radius: 10px;
}

input {
    font-size: 2.5rem;
    width: 80%;
    text-align: center;
    border-radius: 5px;
    border-style: none;
}

button {
    margin: 20px;
}
</style>