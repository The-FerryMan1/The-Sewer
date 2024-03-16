<script setup>
import { ref } from 'vue';

const newText = ref(null);
const emit = defineEmits(['add'])
const handleSubmit = ()=>{
    emit('add', newText.value)
    newText.value = null
}
</script>
 <!-- @submit.prevent="$emit('add', newText)"  -->
<template>
    <form @submit.prevent="handleSubmit" class="flex w-full justify-between items-center">
        <input v-model="newText" class="w-full py-2 px-2 outline-none bg-gray-200 rounded-l-lg " placeholder="Add List" type="text">
        <button class="py-2 w-[10%] px-2 bg-emerald-500 text-white text-center rounded-r-lg  text-base hover:bg-emerald-600 "><img src="../assets/add.png" alt="add" class="h-6 w-6"></button>
    </form>
</template>