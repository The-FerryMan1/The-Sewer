<template>
    <div class="bg-gray-200 w-[95%] h-full rounded-md flex justify-between items-center p-2">
        <div class="flex justify-center gap-2  items-center w-full">
            <span><img src="../assets/list.png" class="h-5 w-5" alt=""></span>
            <p>List: {{ NumberList? NumberList.length:"No item" }}</p>
        </div>
        <div class="flex justify-center gap-2 items-center w-full" >
            <span><img src="../assets/correct.png" class="h-5 w-5" alt="correct"></span>
            <p>Checked: {{ CheckedList?CheckedList.length:"no item" }}</p>
        </div>
        <div class="flex justify-center gap-2 items-center w-full">
            <span><img src="../assets/check.png" class="h-5 w-5"  alt=""></span>
            <p>Unchecked: {{ UnCheckedList? UnCheckedList.length:"no item" }}</p>
        </div>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const count  = defineProps({
    Count: Array
})
const NumberList = computed(()=>{
    return  count.Count
})
const CheckedList = computed(()=>{
    return count.Count ? count.Count.filter((t) => t.done) : count.Count
})
const UnCheckedList = computed(() => {
    return count.Count? count.Count.filter((t) => !t.done): count.Count
})
</script>