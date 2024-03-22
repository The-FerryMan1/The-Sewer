<script setup>
const data = defineProps({
    Data: Array
})

</script>

<template>

  
    <ul v-if="data.Data.length > 0" class=" w-[95%] flex bg-gray-200  p-3 flex-col gap-2 rounded-md font-mono ">
          <li @click="$emit('check', list.id)" v-for="list in data.Data" :key="list.id" class="flex  w-full py-2 justify-between items-center bg-white text-wrap">
                <span class="h-full"><hr :class="list.done ? 'h-full border-2 border-emerald-500 rounded-md':'h-full border-2 border-transparent rounded-md'"></span>
                <p class=" w-1/2 text-center break-words">{{list.text}}</p>
                <button @click="$emit('delete', list.id)" class="me-1"><img src="../assets/delete.png" alt="delte" class=" h-5 w-5"></button>
            </li>
            
    </ul>
    <h1 v-else>The list is empty</h1>

</template>