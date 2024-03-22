
<template>
 
 <main class="w-full h-screen flex flex-col justify-center items-center bg-gray-300">
  <div class=" bg-white sm:w-[30%] w-full flex flex-col justify-start items-start h-full shadow-lg ">
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

  import { ref, onBeforeMount } from 'vue';


// {
//    id:1,
//    text: "List 1",
//    done: true
// },
//  {
//    id: 2,
//    text: "List 2",
//    done: false
// },
// {
//    id: 3,
//    text: "List 3",
//    done: false
// }
  const Lists = ref([]);

  onBeforeMount(()=>{

     const Gamit = JSON.parse(localStorage.getItem('items'))

     if(Gamit){
      console.log(Gamit)
      Lists.value = Gamit 
     }else{
       console.log("null")
     }
   // Lists.value = Gamit  
  })

  const addAdd =(newText)=>{
   if (newText === null) {
      return
  }
  const id = Lists.value.length ? Lists.value[Lists.value.length - 1].id + 1 : 1;
   const newList = { id, text: newText, done: false };
   Lists.value = [...Lists.value, newList]
   localStorage.setItem('items', JSON.stringify(Lists.value))
}
  const handleDelete =(id)=>{
      Lists.value = Lists.value.filter((t)=> t.id!==id);
     localStorage.setItem('items', JSON.stringify(Lists.value))
  }
  const handleCheck = (id)=>{
   const CheckBago = Lists.value.map((list)=> list.id === id? {...list, done: !list.done}: list)
   Lists.value = CheckBago
     localStorage.setItem('items', JSON.stringify(Lists.value))
  }
</script>