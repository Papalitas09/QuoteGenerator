<template>
  <div class="w-3xl h-96 bg-green-500 p-5 flex flex-col justify-evenly items-center gap-5">
    <h2 class="text-5xl">Quotes Generator</h2>

    <div v-if="quote">
      <p class="text-xl text-center">"{{ quote.quote }}"</p>
      <p class="text-lg font-semibold">- {{ quote.author }}</p>
    </div>

    <button class="w-fit p-5 bg-gray-400" @click="RandomQuote">
      Generate Random Quotes!
    </button>
  </div>
</template>

<script setup lang="ts">
type Quote = {
  quote: string
  author: string
  work?: string
  categories?: string[]
} //nah ini penting, pelajarin. sebenarnya masalahnya tuh di ts. Ts itu strict banget cug

const quote = ref<Quote | null>(null)

async function RandomQuote() {
  
    if(quote.value == null){
        const { data, error } = await useFetch<Quote[]>(
        'https://api.api-ninjas.com/v2/randomquotes',
        {
        headers: {
            "X-Api-Key": "cckkQK33ftugrjLbc6iM1g==Yubl53Y5I3urPUGQ" //nanti amanin api key
        },
        method: "GET"
        }
        )
        if (data.value?.[0] && quote.value == null) {
            quote.value = data.value[0]
        } 
    } else {
        quote.value = null
         const { data, error } = await useFetch<Quote[]>(
        'https://api.api-ninjas.com/v2/randomquotes',
        {
        headers: {
            "X-Api-Key": "cckkQK33ftugrjLbc6iM1g==Yubl53Y5I3urPUGQ" //nanti amanin api key
        },
        method: "GET"
        }
        )
        if (data.value?.[0] && quote.value == null) {
            quote.value = data.value[0]
        } 
    }

  
//itu gpt yang buat, pelaajrin lagi sat!!
}
</script>
