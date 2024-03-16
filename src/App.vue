
<template>
 
 <main class="w-100 h-screen flex flex-col justify-center items-center bg-gray-300">
  <div class=" bg-white w-[30%] flex flex-col justify-start items-start h-full shadow-lg ">
     <HeaderTodo/>

     <!-- Add list form -->
     <div class="p-2 w-full">
        <addList @add="addAdd"/>
     </div>

     <!-- list of list -->
     <div class="p-2 w-full h-[100%]  overflow-y-auto flex flex-col justify-start items-center">
         <RenderList :Data="Lists" @delete="handleDelete" @check="handleCheck"/>
     </div>
     <div class="p-2 w-full h-[20%] flex flex-col justify-start items-center">
      <CheckCount :Count="Lists"/>
     </div>

     <FooterMain/>
  </div>
  
 </main>
</template>




<script setup>
  import HeaderTodo from './components/Header-Todo.vue';
  import addList from './components/addList.vue';
  import RenderList from './components/RenderList.vue';
  import CheckCount from './components/CheckCount.vue';
  import FooterMain from'./components/FooterMain.vue';

  import { ref } from 'vue';

  const Lists = ref([
   {
      id:1,
      text: "List 1",
      done: true
   },
    {
      id: 2,
      text: "List 2",
      done: false
   },
   {
      id: 3,
      text: "List 3",
      done: false
   }
  ]);

  const addAdd =(newText)=>{
   if (newText === null) {
      return
  }
  const id = Lists.value.length ? Lists.value[Lists.value.length - 1].id + 1 : 1;
   const newList = { id, text: newText, done: false };
   Lists.value = [...Lists.value, newList]
}
  const handleDelete =(id)=>{
      Lists.value = Lists.value.filter((t)=> t.id!==id);
  }
  const handleCheck = (id)=>{
   const CheckBago = Lists.value.map((list)=> list.id === id? {...list, done: !list.done}: list)
   Lists.value = CheckBago
  }
</script>