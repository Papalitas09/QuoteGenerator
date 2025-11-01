<template>
    <div class="bg-emerald-900 w-full max-h-full gap-2">
        <h3 class="text-lg">{{ response }}</h3>
        <h4 class="text-center text-lg">~Author~</h4>
    </div>
</template>

<script setup lang="ts">
defineProps<{
    response:string
}>()
</script>