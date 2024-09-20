<script setup lang="ts">
const { title, content } = defineProps<{
    title: string;
    content: string;
}>();

</script>
<template>
    <h2 class="text-2xl font-bold mb-2" v-html="title"></h2>
    <p class="text-lg text-[#666] text-justify" v-html="content"></p>
</template>