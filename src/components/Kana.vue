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
    {kana: 'モ', romaji: 'mo', input: '', color: '#000', disabled: false},
    {kana: 'ヤ', romaji: 'ya', input: '', color: '#000', disabled: false},
    {kana: 'ユ', romaji: 'yu', input: '', color: '#000', disabled: false},
    {kana: 'ヨ', romaji: 'yo', input: '', color: '#000', disabled: false},
    {kana: 'ラ', romaji: 'ra', input: '', color: '#000', disabled: false},
    {kana: 'リ', romaji: 'ri', input: '', color: '#000', disabled: false},
    {kana: 'ル', romaji: 'ru', input: '', color: '#000', disabled: false},
    {kana: 'レ', romaji: 're', input: '', color: '#000', disabled: false},
    {kana: 'ロ', romaji: 'ro', input: '', color: '#000', disabled: false},
    {kana: 'ワ', romaji: 'wa', input: '', color: '#000', disabled: false},
    {kana: 'ヲ', romaji: 'wo', input: '', color: '#000', disabled: false},
    {kana: 'ン', romaji: 'n', input: '', color: '#000', disabled: false},
    {kana: 'ガ', romaji: 'ga', input: '', color: '#000', disabled: false},
    {kana: 'ギ', romaji: 'gi', input: '', color: '#000', disabled: false},
    {kana: 'グ', romaji: 'gu', input: '', color: '#000', disabled: false},
    {kana: 'ゲ', romaji: 'ge', input: '', color: '#000', disabled: false},
    {kana: 'ゴ', romaji: 'go', input: '', color: '#000', disabled: false},
    {kana: 'ザ', romaji: 'za', input: '', color: '#000', disabled: false},
    {kana: 'ジ', romaji: 'ji', input: '', color: '#000', disabled: false},
    {kana: 'ズ', romaji: 'zu', input: '', color: '#000', disabled: false},
    {kana: 'ゼ', romaji: 'ze', input: '', color: '#000', disabled: false},
    {kana: 'ゾ', romaji: 'zo', input: '', color: '#000', disabled: false},
    {kana: 'ダ', romaji: 'da', input: '', color: '#000', disabled: false},
    {kana: 'ヂ', romaji: 'di', input: '', color: '#000', disabled: false},
    {kana: 'ヅ', romaji: 'du', input: '', color: '#000', disabled: false},
    {kana: 'デ', romaji: 'de', input: '', color: '#000', disabled: false},
    {kana: 'ド', romaji: 'do', input: '', color: '#000', disabled: false},
    {kana: 'バ', romaji: 'ba', input: '', color: '#000', disabled: false},
    {kana: 'ビ', romaji: 'bi', input: '', color: '#000', disabled: false},
    {kana: 'ブ', romaji: 'bu', input: '', color: '#000', disabled: false},
    {kana: 'ベ', romaji: 'be', input: '', color: '#000', disabled: false},
    {kana: 'ボ', romaji: 'bo', input: '', color: '#000', disabled: false},
    {kana: 'パ', romaji: 'pa', input: '', color: '#000', disabled: false},
    {kana: 'ピ', romaji: 'pi', input: '', color: '#000', disabled: false},
    {kana: 'プ', romaji: 'pu', input: '', color: '#000', disabled: false},
    {kana: 'ペ', romaji: 'pe', input: '', color: '#000', disabled: false},
    {kana: 'ポ', romaji: 'po', input: '', color: '#000', disabled: false},
]);

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