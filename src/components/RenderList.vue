<script setup>
const data = defineProps({
    Data: Array
})

</script>

<template>
    <ul class=" w-[95%] flex bg-gray-200  p-3 flex-col gap-2 rounded-md font-mono ">
          <li @click="$emit('check', list.id)" v-for="list in data.Data" :key="list.id" class="flex  w-full py-2 justify-between items-center bg-white relative">
                <span class="h-full"><hr :class="list.done ? 'h-full border-2 border-emerald-500 rounded-md':'h-full border-2 border-transparent rounded-md'"></span>
                <p class="text-center">{{list.text}}</p>
                <button @click="$emit('delete', list.id)" class="me-1"><img src="../assets/delete.png" alt="delte" class=" h-5 w-5"></button>
            </li>
            
    </ul>
</template>