<template>
    <div class=" w-full md:max-h-full h-fit p-5 items-center justify-center flex flex-col gap-2 md:bg-transparent bg-[#CFFFE2] border-2 md:border-0 hover:shadow-none transition ease-in-out hover:scale-105 duration-300 ">
        <h3 class="text-2xl text-center italic text-white text-shadow-md">"{{ Quote }}"</h3>
        <h3 class="text-center text-xl italic text-white text-shadow-md">~ {{ Author }} ~</h3>
    </div>
</template>

<script setup lang="ts">
defineProps<{
    Quote:string,
    Author:string,
}>()
</script>