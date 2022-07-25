<script setup>
import { store } from './store'

const kana_list = [
    {kana: 'ア', romaji: 'a'},
    {kana: 'イ', romaji: 'i'},
    {kana: 'エ', romaji: 'e'},
    {kana: 'ウ', romaji: 'u'},
    {kana: 'オ', romaji: 'o'}
]

</script>

<template>
    <div>
        <div v-for="item in kana_list">
            <div>{{item.kana}}</div>
        </div>
        <button @click="store.kana_visible = !store.kana_visible">done</button>
    </div>
</template>