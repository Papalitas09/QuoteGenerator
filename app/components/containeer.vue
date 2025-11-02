
<template>
  <div class="w-3xl md:h-96 h-full  bg-[#A2D5C6] p-5 flex flex-col justify-center md:gap-2 gap-8 items-center shadow-[7px_12px_0px_4px_#000000] rounded-3xl ">
    <h2 class="text-5xl font-extrabold text-white text-shadow-md cursor-pointer text-center hover:scale-105 transition ease-in-out duration-300">QUOTES GENERATOR</h2>
    <response v-if="quote" :Quote="quote.quote" :Author="quote.author"/>
    <button class="w-fit p-5 bg-[#CFFFE2] shadow-[7px_12px_0px_4px_#000000] hover:shadow-none transition ease-in-out hover:scale-105 cursor-pointer text-xl text-white text-shadow-md duration-300 " @click="RandomQuote()">
      Generate Random Quotes!
    </button>
  </div>
  <h2 class="absolute bottom-2 italic font-bold">~~~ Made by <NuxtLink to="https://github.com/Papalitas09/" class="cursor-pointer hover:text-slate-400 transition duration-300">Haiiro</NuxtLink> | <NuxtLink to="https://github.com/Papalitas09/" class="cursor-pointer hover:text-slate-400 transition duration-300">Papalitas</NuxtLink> ~~~</h2>
</template>

<script setup lang="ts">
type Quote = {
  quote: string
  author: string
} //nah ini penting, pelajarin. sebenarnya masalahnya tuh di ts. Ts itu strict banget cug

const quote = ref<Quote | null>(null)
const config = useRuntimeConfig()
 async function RandomQuote(){
   const { data, error, refresh } = await useFetch<Quote[]>(
        'https://api.api-ninjas.com/v2/randomquotes',
        {
        headers: {
            "X-Api-Key": config.public.key_mama  //nanti amanin api key
        },
        method: "GET"
        }
        )
        if (data.value?.[0]) {
          refresh()
          quote.value = data.value[0]
          console.log(quote.value)
        }  else {
            console.log(error)
        }
 }
</script>
