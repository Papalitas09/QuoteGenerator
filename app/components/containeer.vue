<template>
    <div class="w-3xl h-96 bg-green-500 p-5 flex-col justify-evenly flex items-center gap-5">
        <h2 class="text-5xl ">Quotes Generator</h2>
        <Response response="e"/>
        <button class="w-fit p-5 bg-gray-400 " @click="RandomQuote()">Generete Random Quotes!</button>
    </div>
</template>

<script setup lang="ts">
const quote = ref('')
async function RandomQuote(){
    const {data, pending, error} = await useFetch('https://api.api-ninjas.com/v2/randomquotes', {
        headers:{
            "x-api-key": 'cckkQK33ftugrjLbc6iM1g==Yubl53Y5I3urPUGQ'
        },
        method: "GET"
    })
    
}

</script>