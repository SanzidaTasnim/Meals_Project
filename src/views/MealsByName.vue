<template>
   <div class="flex p-8 justify-center">
      <input 
         type="text" 
         class="rounded border-2 border-gray-200 w-[800px]" 
         placeholder="Search For Meals" 
         v-model="keyword"
         @change="searchByName"
      />
   </div>
   <div>
      <pre>
         {{ meals }}
      </pre>
   </div>
</template>

<script setup>
import { ref } from 'vue';
import { computed } from "@vue/reactivity"
import store from '../store';


   const keyword = ref('');
   const meals = computed(() => store.state.searchedMeals);

   function searchByName(){
      store.dispatch('searchMeals', keyword);
   }
</script>
