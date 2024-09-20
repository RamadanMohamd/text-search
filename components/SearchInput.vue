<script setup lang="ts">
import type { InputHTMLAttributes } from 'vue';
import { defineEmits } from 'vue';

const { searchText } = defineProps<{
    searchText: string;
}>();


const emit = defineEmits<{
    (e: 'updateSearchText', value: string): void;
}>();

const updateSearchText = ($event: Event) => {
    const target = $event.target as HTMLInputElement;
    emit('updateSearchText', target.value);
}

</script>

<template>
    <div class="relative w-full">
        <input id="input" type="text" @input="updateSearchText" :value="searchText" placeholder="Search..."
            class="w-full h-[48px] rounded px-4 py-2 border border-slate-300 focus:outline-none focus:shadow-md"
            autocomplete="off" />
        <CloseIcon @click="emit('updateSearchText', '')"
            :class="{ 'absolute right-3 top-1/2 -translate-y-1/2 cursor-pointer opacity-0 scale-0 duration-300': true, 'opacity-100 scale-100': searchText }" />
    </div>
</template>